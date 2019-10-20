---
title: Łączenie aktualizacji modelu UML przy użyciu transakcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657605"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Łączenie aktualizacji modelu UML za pomocą transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas definiowania rozszerzenia dla projektantów UML w programie Visual Studio, można grupować kilka zmian w pojedynczą transakcję o nazwie *połączonego kontekstu cofania*. Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Domyślnie każda modyfikacja wprowadzana przez kod do modelu może być oddzielnie cofnięta przez użytkownika. Na przykład, jeśli zdefiniujesz polecenie menu, które zamienia nazwy dwóch klas UML, użytkownik może wywołać polecenie, a następnie wykonać pojedyncze cofanie. Spowoduje to cofnięcie zmiany do jednej nazwy, ale nie drugiego, pozostawiając model w stanie niezamierzonym.

 Aby tego uniknąć, kod może wykonać serię zmian w ramach transakcji. Dzięki temu zmiany mogą wyglądać jak jedna zmiana dla użytkownika. Kolejne polecenie Cofnij spowoduje cofnięcie całej serii.

 Dodatkową korzyścią jest to, że kod może cofnąć częściowo pełny zestaw zmian, zwracając wyjątek lub przerywając transakcję.

## <a name="to-group-changes-into-a-single-transaction"></a>Aby grupować zmiany w pojedynczą transakcję
 Upewnij się, że odwołania do projektu zawierają ten zestaw .NET:

 **Microsoft. VisualStudio. Modeling. Sdk. [wersja]. dll**

 Wewnątrz klasy Zadeklaruj zaimportowaną właściwość, która ma typ <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 W metodzie modyfikującej model należy ująć zmiany w transakcji:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Zwróć uwagę na następujące kwestie:

- Zawsze należy uwzględnić `Commit()` na końcu transakcji. Jeśli transakcja zostanie usunięta bez zatwierdzenia, transakcja zostanie wycofana. Oznacza to, że model zostanie przywrócony do stanu na początku transakcji.

- Jeśli wystąpi wyjątek, który nie jest przechwytywany wewnątrz transakcji, transakcja zostanie wycofana. Jest to częsty wzorzec otaczający blok `using` transakcji wewnątrz bloku `try…catch`.

- Można zagnieżdżać transakcje.

- Do `BeginTransaction()` można podać dowolną nazwę, która nie jest pusta.

- Te transakcje mają wpływ tylko na magazyn modelu UML. Transakcje modelowania nie wpływają na: zmienne, sklepy zewnętrzne, takie jak pliki i bazy danych, diagramy warstwowe i modele kodu.

## <a name="example"></a>Przykład

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>Zobacz też
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md) [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [rozszerzając modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md)
