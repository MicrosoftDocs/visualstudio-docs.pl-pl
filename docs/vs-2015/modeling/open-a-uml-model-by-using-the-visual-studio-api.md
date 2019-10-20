---
title: Otwórz model UML przy użyciu interfejsu API programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668504"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można również otworzyć modele i diagramy w interfejsie użytkownika programu Visual Studio za pomocą interfejsu API.

 Jeśli chcesz tylko odczytywać model w kodzie programu bez udostępniania go użytkownikowi, możesz użyć następujących metod:

- Magistrala modelu programu Visual Studio umożliwia dostęp do modeli i elementów w ramach nich oraz zapewnia standardową metodę tworzenia linków między modelami i innymi. Aby uzyskać więcej informacji, zobacz [integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Model można otworzyć w trybie tylko do odczytu. Aby uzyskać więcej informacji, zobacz [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Showing"></a>Otwieranie modeli i diagramów w programie Visual Studio
 Aby otworzyć model w interfejsie użytkownika, należy użyć standardowego interfejsu API programu Visual Studio `EnvDTE.DTE`. Istnieją dwa przydatne rzuty, które można wykonywać na elementach projektu modelowania:

- `EnvDTE.Project` można rzutować do i z `IModelingProject`, jeśli projekt jest projektem modelowania i jeśli projekt jest ładowany w bieżącej domenie aplikacji.

- `EnvDTE.ProjectItem` można rzutować do i z `IDiagramContext`, jeśli element jest diagramem UML.

  W poniższym przykładzie projekt powinien importować te odwołania:

- EnvDTE

- Microsoft. VisualStudio. ArchitectureTools. rozszerzalność

- Microsoft. VisualStudio. Modeling. Sdk. nowszym

- Microsoft. VisualStudio. Modeling. Sdk. diagramy. nowszym

- Microsoft. VisualStudio. Shell. unzmienna. nowszym

- Microsoft. VisualStudio. UML. Interfaces

- System. ComponentModel. kompozycji

  W tym przykładzie zostanie otwarty model UML w programie Visual Studio:

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 W rozszerzeniu programu Visual Studio można wykonać tę deklarację, aby uzyskać dostęp do dostawcy usług hosta:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 W metodzie można uzyskać dostęp do projektu, na przykład bieżący projekt:

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>Zobacz też
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md) — tworzenie [modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
