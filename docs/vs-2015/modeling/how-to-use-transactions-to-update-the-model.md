---
title: 'Instrukcje: Użycie transakcji do aktualizacji modelu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bbc09543d0ee0297678d3f205becc55a6b6d7714
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181505"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Instrukcje: Użycie transakcji do aktualizacji modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transakcje upewnij się, że zmiany wprowadzone do magazynu są traktowane jako grupa. Zmiany, które są grupowane może być przekazana lub wycofana jako pojedyncza jednostka.  
  
 Zawsze, gdy kod programu modyfikuje, dodaje lub usuwa dowolnego elementu w Store w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wizualizacji i modelowania SDK, należy wykonać czynności wewnątrz transakcji. Musi być aktywne wystąpienie <xref:Microsoft.VisualStudio.Modeling.Transaction> skojarzone z Store, w przypadku zmiany. Dotyczy to wszystkich elementów modelu, relacje, kształty, diagramy i ich właściwości.  
  
 Mechanizm transakcji pomaga uniknąć niespójne stanów. Jeśli wystąpi błąd podczas wykonywania transakcji, wszystkie zmiany zostaną wycofane. Gdy użytkownik wykonuje polecenie Cofnij, każda transakcja ostatnie jest traktowany jako pojedynczy krok. Użytkownik nie można cofnąć części ostatnią zmianę, chyba że jawnie je umieścić w oddzielnych transakcji.  
  
## <a name="opening-a-transaction"></a>Otwieranie transakcji  
 Najwygodniejsza metoda zarządzania transakcji jest `using` instrukcji ujęta w `try...catch` instrukcji:  
  
```  
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
  
 Jeśli wyjątek, który uniemożliwia końcowe `Commit()` występuje podczas wprowadzania zmian, Store zostaną zresetowane do jego poprzedniego stanu. Pomaga to upewnić się, że błędy nie spowodują pozostawienia modelu w stanie niespójnym.  
  
 Można wprowadzić dowolną liczbę zmian w jednej transakcji. Możesz otworzyć nowe transakcje w aktywnej transakcji. Transakcji zagnieżdżonych musi przekazać ani wycofać się przed zakończeniem zawierającego transakcji. Aby uzyskać więcej informacji, zobacz przykład <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> właściwości.  
  
 Aby zmiany były trwałe, należy `Commit` transakcji, zanim zostanie on usunięty. Jeśli wystąpi wyjątek, który nie jest wyłapywany wewnątrz transakcji, Store zostaną zresetowane do stanu przed wdrożeniem zmian.  
  
## <a name="rolling-back-a-transaction"></a>Wycofywanie transakcji  
 Aby upewnić się, że Store pozostaje w lub powraca do stanu przed transakcji, można użyć jednej z tych taktyka:  
  
1. Zgłoś wyjątek, który nie jest wyłapywany wewnątrz zakresu transakcji.  
  
2. Jawnie Wycofaj tę transakcję:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Transakcje nie wpływają na obiekty innego niż Store  
 Transakcje określają tylko stan Store. Nie można ich cofnąć częściowe zmiany, które zostały wprowadzone do elementów zewnętrznych, takich jak pliki, bazy danych lub obiektów, które zostały zadeklarowane za pomocą zwykłego typów poza definicji DSL.  
  
 Wyjątek mogą pozostać taka zmiana niespójne z Store, powinno dotyczyć tę możliwość w obsłudze wyjątków. Jednym ze sposobów, aby upewnić się, że zasoby zewnętrzne pozostają zsynchronizowane z obiektami Store jest połączenie każdego obiektu zewnętrznego do elementu w sklepie przy użyciu programów obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Ogień reguły na końcu transakcji  
 Na końcu transakcji przed transakcja jest usuwana, uruchamiane są reguły dołączone do elementów w magazynie. Każda reguła jest metoda, która jest stosowana do elementu modelu, który został zmieniony. Na przykład istnieją reguły z "Napraw", które aktualizują stan kształtu, gdy zmieniono jego element modelu, a które Utwórz kształt, po utworzeniu elementu modelu. Nie ma żadnej uruchomieniu którego określonej kolejności. Zmiany wprowadzone przez regułę można wyzwalać inną regułę.  
  
 Można zdefiniować własne reguły. Aby uzyskać więcej informacji na temat reguł zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
 Zasady nie uruchamiają się po cofania, powtórz lub polecenie wycofania.  
  
## <a name="transaction-context"></a>Kontekst transakcji  
 Każda transakcja ma słownika, w którym można przechowywać wszystkie informacje, które mają:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Jest to szczególnie przydatne do przesyłania informacji między regułami.  
  
## <a name="transaction-state"></a>Stan transakcji  
 W niektórych przypadkach, czego potrzebujesz, aby uniknąć propagowanie zmian, jeśli zmiana jest spowodowany przez cofania i ponawiania transakcji. Może to nastąpić, na przykład jeśli piszesz program obsługi wartości właściwości, który można zaktualizować innej wartości w Store. Ponieważ operacja cofania resetuje wszystkie wartości w Store do poprzedniego stanu, nie jest konieczne do obliczenia zaktualizowanymi wartościami. Użyj tego kodu:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Zasady można uruchamiał się po magazynie początkowo jest ładowany z pliku. Aby uniknąć, odpowiadać na te zmiany, należy użyć:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```
