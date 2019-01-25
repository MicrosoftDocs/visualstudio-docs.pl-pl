---
title: Łączenie aktualizacji modelu UML za pomocą transakcji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 640217b9ee9a8cb51ed11931d0d66b2c98e0a165
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803409"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Łączenie aktualizacji modelu UML za pomocą transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zdefiniowaniu rozszerzenia projektantów UML w programie Visual Studio można zgrupować kilka zmian w pojedynczą transakcję o nazwie *kontekst połączonego cofania*. Aby dowiedzieć się, które wersje programu Visual Studio obsługują modeli UML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Domyślnie każda modyfikacja kodu sprawia, że model może zostać oddzielnie cofnięta przez użytkownika. Na przykład jeśli zdefiniujesz polecenie menu, które zamienia nazwy dwóch klas UML, użytkownik może wywołać polecenie, a następnie wykonać pojedynczą czynność cofnięcia. Czy to cofnie zmianę do jednej nazwy, ale nie drugiej, pozostawiając Twój model w niezamierzonym stanie.  
  
 Aby tego uniknąć, kod może wykonać szereg zmian w obrębie transakcji. To sprawia, że zmiany wyglądają jak jedna zmiana dla użytkownika. Kolejne polecenie cofnięcia spowoduje cofnięcie całej serii.  
  
 Dodatkową korzyścią jest to, że kod może cofnąć częściowo wypełnione zestawy zmian przez wyrzucanie wyjątku lub przerywanie transakcji.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Aby pogrupować zmiany w pojedynczą transakcję  
 Upewnij się, że odwołania projektu obejmują ten zestaw .NET:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version].dll**  
  
 Wewnątrz klasy, należy zadeklarować zaimportowaną właściwość typu <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 W metodzie, która modyfikuje model należy ująć zmiany w transakcji:  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Zapamiętaj poniższe:  
  
-   Musisz zawsze dołączać `Commit()` na końcu transakcji. Jeśli transakcja jest usuwana bez zatwierdzenia, transakcja zostanie wycofana. Oznacza to, że model zostanie przywrócony do jego stanu na początku transakcji.  
  
-   Jeśli wystąpi wyjątek, który nie jest wyłapywany wewnątrz transakcji, transakcja zostanie wycofana. To częsty wzór, aby ująć `using` transakcji wewnątrz bloku `try…catch` bloku.  
  
-   Transakcje można zagnieżdżać.  
  
-   Możesz podać dowolną nazwę niepustych `BeginTransaction()`.  
  
-   Tylko Store modelu UML ma wpływ tych transakcje. Nie wpływają na transakcje modelowania: zmienne, zewnętrzne magazyny takie jak pliki i baz danych, diagramy warstw, a kod modeli.  
  
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
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)   
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
