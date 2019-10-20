---
title: 'Porady: użycie transakcji do aktualizacji modelu'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a08ea67477f42008c35b6f141351beaeee03d27b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661134"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Porady: użycie transakcji do aktualizacji modelu
W przypadku transakcji upewnij się, że zmiany wprowadzone w sklepie są traktowane jako Grupa. Zmiany pogrupowane mogą być zatwierdzane lub wycofywane jako pojedyncza jednostka.

 Za każdym razem, gdy kod programu modyfikuje, dodaje lub usuwa każdy element ze sklepu w programie Visual Studio Wizualizacja i Modeling SDK, musi to zrobić w ramach transakcji. W przypadku zmiany należy mieć aktywne wystąpienie <xref:Microsoft.VisualStudio.Modeling.Transaction> skojarzone z magazynem. Dotyczy to wszystkich elementów modelu, relacji, kształtów, diagramów i ich właściwości.

 Mechanizm transakcji pomaga uniknąć niespójnych Stanów. Jeśli wystąpi błąd w trakcie transakcji, wszystkie zmiany zostaną wycofane. Jeśli użytkownik wykonuje polecenie Cofnij, każda Ostatnia transakcja jest traktowana jako pojedynczy krok. Użytkownik nie może cofnąć części ostatniej zmiany, chyba że jawnie umieści je w osobnych transakcjach.

## <a name="opening-a-transaction"></a>Otwieranie transakcji
 Najbardziej wygodną metodą zarządzania transakcjami jest wyrażenie `using` ujęte w instrukcji `try...catch`:

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Jeśli wyjątek, który uniemożliwia końcową `Commit()` występuje podczas wprowadzania zmian, magazyn zostanie zresetowany do poprzedniego stanu. Dzięki temu można upewnić się, że błędy nie opuszczają modelu w stanie niespójnym.

 Można wprowadzić dowolną liczbę zmian w jednej transakcji. Możesz otworzyć nowe transakcje wewnątrz aktywnej transakcji. Transakcje zagnieżdżone muszą zostać zatwierdzone lub wycofane przed zakończeniem transakcji zawierającej. Aby uzyskać więcej informacji, zobacz przykład właściwości <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>.

 Aby zmiany były trwałe, należy `Commit` transakcji przed jej usunięciem. Jeśli wystąpi wyjątek, który nie jest przechwytywany w ramach transakcji, magazyn zostanie zresetowany do stanu sprzed zmian.

## <a name="rolling-back-a-transaction"></a>Wycofywanie transakcji
 Aby upewnić się, że magazyn pozostanie w lub powróci do stanu sprzed transakcji, możesz użyć jednego z następujących taktykę:

1. Zgłoś wyjątek, który nie jest przechwytywany w zakresie transakcji.

2. Jawnie Wycofaj transakcję:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Transakcje nie wpływają na obiekty spoza magazynu
 Transakcje określają tylko stan magazynu. Nie mogą cofnąć zmian częściowych, które zostały wprowadzone do elementów zewnętrznych, takich jak pliki, bazy danych lub obiekty zadeklarowane przy użyciu zwykłych typów poza definicją DSL.

 Jeśli wyjątek może opuścić takie zmiany, które są niespójne ze sklepem, należy zaradzić sobie z tą możliwością w programie obsługi wyjątków. Jednym ze sposobów, aby upewnić się, że zasoby zewnętrzne pozostają zsynchronizowane z obiektami magazynu, jest podłączane każdy obiekt zewnętrzny do elementu w magazynie przy użyciu programów obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Reguły wyzwalane na końcu transakcji
 Na koniec transakcji przed usunięciem transakcji reguły dołączone do elementów w sklepie są generowane. Każda reguła jest metodą, która jest stosowana do elementu modelu, który został zmieniony. Na przykład istnieją reguły "Napraw", które aktualizują stan kształtu, gdy jego element modelu został zmieniony, i który tworzy kształt po utworzeniu elementu modelu. Nie określono kolejności wyzwalania. Zmiana wprowadzona przez regułę może wywołać inną regułę.

 Możesz definiować własne reguły. Aby uzyskać więcej informacji na temat reguł, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

 Reguły nie uruchamiają się po wykonaniu polecenia Cofnij, ponów lub Wycofaj.

## <a name="transaction-context"></a>Kontekst transakcji
 Każda transakcja ma słownik, w którym można przechowywać potrzebne informacje:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Jest to szczególnie przydatne w przypadku przenoszenia informacji między regułami.

## <a name="transaction-state"></a>Stan transakcji
 W niektórych przypadkach należy unikać propagacji zmiany, jeśli zmiana jest spowodowana cofnięciem lub ponownym wykonaniem transakcji. Taka sytuacja może wystąpić, jeśli na przykład napiszesz procedurę obsługi wartości właściwości, która może aktualizować inną wartość w sklepie. Ponieważ operacja Cofnij resetuje wszystkie wartości ze sklepu do ich poprzednich Stanów, nie trzeba obliczać zaktualizowanych wartości. Użyj tego kodu:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Reguły mogą być wyzwalane po początkowym załadowaniu magazynu z pliku. Aby uniknąć reakcji na te zmiany, użyj:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```