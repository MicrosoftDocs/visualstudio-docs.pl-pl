---
title: Pobieranie elementów modelu UML z IDataObject | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ded3910e74120433038132eb0135a869ea92d58d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755101"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Pobieranie elementów modelu UML z elementu IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy użytkownik przeciągnie elementy z dowolnego źródła na diagramie, przeciągane elementy zostaną zakodowane w `System.Windows.Forms.IDataObject`. Kodowanie jest zależne od typu obiektu źródłowego. Poniższy fragment przedstawia sposób pobierania elementów, gdy źródłem jest UML diagram.  
  
> [!NOTE]
>  Większość operacji, które należy wykonać na modelach UML można wykonać przy użyciu typów w zdefiniowanych zestawach **Microsoft.VisualStudio.Uml.Interfaces** i  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Ale w tym celu należy użyć niektórych klas, które są częścią implementacji narzędzia do modelowania UML. Na przykład `ShapeElement` w tym fragmencie nie jest taki sam jak UML `IShape`. Aby zmniejszyć ryzyko wprowadzenia modelu UML i diagramów w niespójnym stanie, są lepiej unikać stosowania metod na tych klasach implementacji, poza przypadkami, gdy nie ma żadnej alternatywy.  
  
## <a name="code-sample"></a>Przykładowy kod  
 Projekt musi odwoływać się do następujących [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] zestawów:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]**  
  
 **System.Windows.Forms**  
  
```  
using Microsoft.VisualStudio.Modeling;    
  // for ElementGroupPrototype  
using Microsoft.VisualStudio.Modeling.Diagrams;    
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs  
…   
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
                  (DiagramDragEventArgs dragEvent)  
  {  
     //ElementGroupPrototype is the container for  
     //dragged and copied elements and toolbox items.  
     ElementGroupPrototype prototype =  
        dragEvent.Data.  
        GetData(typeof(ElementGroupPrototype))  
                     as ElementGroupPrototype;  
     // Locate the originals in the implementation store.  
     IElementDirectory implementationDirectory =   
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
     return  prototype.ProtoElements.Select(  
       prototypeElement =>   
       {  
          ModelElement element = implementationDirectory  
                .FindElement(prototypeElement.ElementId);  
          ShapeElement shapeElement = element as ShapeElement;  
          if (shapeElement != null)  
          {   
            // Dragged from a diagram.  
            return shapeElement.ModelElement as IElement;  
          }  
          else  
          {   
            // Dragged from UML Model Explorer.  
            return element as IElement;  
          }  
        });  
    }  
```  
  
 Aby uzyskać więcej informacji na temat `ElementGroupPrototype` i `Store` , w której realizowane są narzędzia modelowania UML, zobacz [zestawu Modeling SDK for Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)   
 [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
