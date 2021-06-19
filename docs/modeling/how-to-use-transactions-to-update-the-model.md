---
title: 'Porady: użycie transakcji do aktualizacji modelu'
description: Dowiedz się, że transakcje upewniają się, że zmiany wprowadzone w magazynie są traktowane jako grupa i jak używać transakcji do aktualizowania modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e91e569573076d1614a9fa946b67f3bda01e6fba
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390545"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Porady: użycie transakcji do aktualizacji modelu
Transakcje upewniają się, że zmiany wprowadzone w magazynie są traktowane jako grupa. Pogrupowane zmiany można zatwierdzona lub wycofana jako pojedyncza jednostka.

 Za każdym razem, gdy kod programu modyfikuje, dodaje lub usuwa dowolny element w magazynie w zestawie SDK wizualizacji i modelowania usługi Visual Studio, musi to zrobić w ramach transakcji. W przypadku zmiany musi być aktywne wystąpienie klasy skojarzone z <xref:Microsoft.VisualStudio.Modeling.Transaction> magazynem. Dotyczy to wszystkich elementów modelu, relacji, kształtów, diagramów i ich właściwości.

 Mechanizm transakcji pomaga uniknąć niespójnych stanów. Jeśli podczas transakcji wystąpi błąd, wszystkie zmiany zostaną wycofane. Jeśli użytkownik wykonuje polecenie Cofnij, każda ostatnia transakcja jest traktowana jako pojedynczy krok. Użytkownik nie może cofnąć części ostatniej zmiany, chyba że jawnie umieścisz je w oddzielnych transakcjach.

## <a name="opening-a-transaction"></a>Otwieranie transakcji
 Najbardziej wygodną metodą zarządzania transakcją jest instrukcja ujęta `using` w `try...catch` instrukcje :

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

 Jeśli podczas zmian wystąpi wyjątek uniemożliwiający ostateczny wynik, magazyn zostanie zresetowany `Commit()` do poprzedniego stanu. Pomaga to upewnić się, że błędy nie pozostawiają modelu w niespójnym stanie.

 W ramach jednej transakcji można wprowadzić dowolną liczbę zmian. Nowe transakcje można otwierać wewnątrz aktywnej transakcji. Zagnieżdżone transakcje muszą zostać zatwierdzone lub wycofane przed zakończeniem transakcji zawierającej. Aby uzyskać więcej informacji, zobacz przykład dla <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> właściwości .

 Aby zmiany stały, należy `Commit` transakcję przed ich usunięcia. Jeśli wystąpi wyjątek, który nie zostanie przechwycony wewnątrz transakcji, magazyn zostanie zresetowany do stanu przed zmianami.

## <a name="rolling-back-a-transaction"></a>Wycofywanie transakcji
 Aby upewnić się, że magazyn pozostaje w stanie lub powraca do stanu przed transakcją, można użyć jednej z tych taktyk:

1. Zgłasza wyjątek, który nie jest przechwycony wewnątrz zakresu transakcji.

2. Jawne wycofywanie transakcji:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Transakcje nie mają wpływu na obiekty bez magazynu
 Transakcje określają tylko stan magazynu. Nie mogą cofnąć częściowych zmian wprowadzonych w elementach zewnętrznych, takich jak pliki, bazy danych lub obiekty, które zostały zadeklarowane za pomocą zwykłych typów poza definicją DSL.

 Jeśli wyjątek może pozostawić taką zmianę niezgodną z magazynem, należy sobie z tym poradzić w obsłudze wyjątków. Jednym ze sposobów, aby upewnić się, że zasoby zewnętrzne pozostają zsynchronizowane z obiektami Store, jest parowanie każdego obiektu zewnętrznego z elementem w magazynie przy użyciu programów obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Reguły są wyzjemniane po zakończeniu transakcji
 Na koniec transakcji, przed transakcji jest usuwany, reguły dołączone do elementów w magazynie są wyzrzuty. Każda reguła jest metodą, która jest stosowana do elementu modelu, który uległ zmianie. Istnieją na przykład reguły "naprawiania", które aktualizują stan kształtu po zmianie jego elementu modelu i tworzą kształt po utworzeniu elementu modelu. Nie ma określonej kolejności wyzwalania. Zmiana dokonana przez regułę może wyzć inną regułę.

 Możesz zdefiniować własne reguły. Aby uzyskać więcej informacji na temat reguł, zobacz [Odpowiadanie na zmiany i propagowanie ich.](../modeling/responding-to-and-propagating-changes.md)

 Reguły nie są wyzłaszane po cofnięcie, ponownego wycofyniu lub wycofaniu polecenia.

## <a name="transaction-context"></a>Kontekst transakcji
 Każda transakcja ma słownik, w którym można przechowywać dowolne informacje:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Jest to szczególnie przydatne w przypadku przesyłania informacji między regułami.

## <a name="transaction-state"></a>Stan transakcji
 W niektórych przypadkach należy unikać propagacji zmiany, jeśli zmiana jest spowodowana przez cofnięcie lub ponownego użycia transakcji. Może się tak zdarzyć na przykład w przypadku napisania procedury obsługi wartości właściwości, która może zaktualizować inną wartość w magazynie. Ponieważ operacja cofania resetuje wszystkie wartości w magazynie do ich poprzednich stanów, nie trzeba obliczać zaktualizowanych wartości. Użyj tego kodu:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Reguły mogą być ładowane, gdy magazyn jest początkowo ładowany z pliku. Aby uniknąć reagowania na te zmiany, użyj:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
