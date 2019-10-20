---
title: Pobieranie elementów modelu UML z IDataObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666077"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Pobieranie elementów modelu UML z elementu IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy użytkownik przeciąga elementy z dowolnego źródła na diagram, przeciągane elementy są kodowane w `System.Windows.Forms.IDataObject`. Kodowanie zależy od typu obiektu źródłowego. Poniższy fragment ilustruje sposób pobierania elementów, gdy źródłem jest diagram UML.

> [!NOTE]
> Większość operacji, które należy wykonać w modelach UML, można wykonać przy użyciu typów zdefiniowanych w zestawach **Microsoft. VisualStudio. UML. Interfaces** i **Microsoft. VisualStudio. ArchitectureTools. rozszerzalności**. Ale w tym celu należy użyć niektórych klas, które są częścią implementacji narzędzi do modelowania UML. Na przykład `ShapeElement` w tym fragmencie nie jest taka sama jak `IShape` UML. Aby zmniejszyć ryzyko umieszczenia modelu UML i diagramów w niespójnym stanie, lepiej jest unikać używania metod w tych klasach implementacji, z wyjątkiem sytuacji, gdy nie ma żadnych alternatyw.

## <a name="code-sample"></a>Przykładowy kod
 Projekt musi odwoływać się do następujących zestawów [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]:

 **Microsoft. VisualStudio. Modeling. Sdk. nowszym**

 **Microsoft. VisualStudio. Modeling. Sdk. diagramy. nowszym**

 **System. Windows. Forms**

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

 Aby uzyskać więcej informacji na temat `ElementGroupPrototype` i `Store`, w których zaimplementowano narzędzia modelowania UML, zobacz [Modeling SDK for Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Zobacz też
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md) [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
