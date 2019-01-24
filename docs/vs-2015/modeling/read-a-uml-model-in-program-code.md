---
title: Odczytywanie modelu UML w kodzie programu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8e90b66288d15abdaf85c519bd89deb6262e4363
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758673"
---
# <a name="read-a-uml-model-in-program-code"></a>Odczytywanie modelu UML w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz załadować UML model i jego diagramy za pomocą interfejsu API UML.  
  
##  <a name="Reading"></a> Czytanie modelu w kodzie programu  
 Dostęp do zawartości modelu bez pokazywania go w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie, użyj `ModelingProject.LoadReadOnly()`.  
  
 Na przykład:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Jeśli chcesz odczytać kształty na diagramie, możesz przeczytać projekt, a następnie diagram.  
  
 Na przykład:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Alternatywne metody  
 W przypadku wielu aplikacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus pozwala na odwołanie do modeli i elementów wewnątrz nich z większą niezawodnością i elastycznością niż z metod opisanych w tym temacie. Zapewnia standardową metodę tworzenia łączy między dowolnymi elementami w tych samych lub różnych modelach. Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Można również otworzyć modele i schematy w interfejsie użytkownika za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu API. Aby uzyskać więcej informacji, zobacz [Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
##  <a name="Standalone"></a> Aplikacje autonomiczne  
 W przykładzie w poprzedniej sekcji będzie działać w rozszerzeniach programu Visual Studio. Istnieje możliwość odczytu modelu w aplikacji autonomicznej, ale należy dodać pewne odwołania do usługi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu.  
  
> [!NOTE]
>  Szczegóły sposobu czytania modelu w aplikacji autonomicznej prawdopodobnie może ulec zmianie w przyszłych wersjach produktu. Niektóre funkcje, które są dostępne w bieżącej wersji nie może być dostępna w przyszłych wersjach.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Aby dodać odwołania do odczytu modelu w aplikacji autonomicznej.  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, w którym jest kompilowana aplikacja, a następnie kliknij przycisk **właściwości**. W edytorze właściwości w **aplikacji** kartę, należy ustawić **platformę docelową** do wymaganej wersji systemu .NET Framework.  
  
2. Dodaj [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] odwołania potrzebne do uzyskania dostępu do modeli UML, zazwyczaj:  
  
   -   Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. Oprócz odniesień wymienionych w poprzednich sekcjach, Dodaj następujące odwołania do projektu z **\Common7\IDE\PrivateAssemblies programu Visual Studio [wersja] \Program Files\Microsoft**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Jeśli chcesz odczytać diagramy w aplikacji może potrzebować także tych odwołań:  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
