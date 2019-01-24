---
title: Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 21f9b02b84644bd748c88e9d08647fa7d57d951b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763340"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można również otworzyć modele i schematy w interfejsie użytkownika programu Visual Studio za pomocą interfejsu API.  
  
 Jeśli chcesz tylko do odczytu modelu w kodzie programu bez uwidaczniania tego użytkownika, można użyć następujących metod:  
  
-   Visual Studio Model Bus pozwala uzyskiwać dostęp do modeli i elementów wewnątrz nich i zapewnia standardową metodę tworzenia łącza między modelem jednego i drugiego. Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Model można otworzyć w trybie tylko do odczytu. Aby uzyskać więcej informacji, zobacz [odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Showing"></a> Otwieranie diagramów i modeli w programie Visual Studio  
 Aby otworzyć model w interfejsie użytkownika, należy użyć standardowego interfejsu API programu Visual Studio `EnvDTE.DTE`. Istnieją dwie przydatne wzory, które można wykonywać do modelowanie elementów projektu:  
  
- `EnvDTE.Project` można rzutować do i z `IModelingProject`, jeśli projekt jest projektem modelowania i jeżeli projekt jest ładowany w bieżącej domenie aplikacji.  
  
- `EnvDTE.ProjectItem` można rzutować do i z `IDiagramContext`, jeśli element jest diagramem UML.  
  
  W poniższym przykładzie projekt powinien zaimportować te odwołania:  
  
- EnvDTE  
  
- Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
- Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
- Microsoft.VisualStudio.Shell.Immutable. [wersja]  
  
- Microsoft.VisualStudio.Uml.Interfaces  
  
- System.ComponentModel.Composition  
  
  W tym przykładzie otwiera modelu UML w programie Visual Studio:  
  
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
  
 W rozszerzeniu Visual Studio można dokonać tej deklaracji w celu uzyskania dostępu do hosta usługodawcy:  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 W metodzie uzyskujesz dostęp do projektu, na przykład bieżącego projektu:  
  
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
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
