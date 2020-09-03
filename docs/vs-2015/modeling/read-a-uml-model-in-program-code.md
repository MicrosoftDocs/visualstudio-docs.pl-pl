---
title: Odczytywanie modelu UML w kodzie programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671309"
---
# <a name="read-a-uml-model-in-program-code"></a>Odczytywanie modelu UML w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz załadować model UML i jego diagramy za pomocą interfejsu API UML.

## <a name="reading-a-model-in-program-code"></a><a name="Reading"></a> Odczytywanie modelu w kodzie programu
 Aby uzyskać dostęp do zawartości modelu bez wyświetlania go w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie, użyj `ModelingProject.LoadReadOnly()` .

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

 Jeśli chcesz odczytać kształty na diagramie, należy odczytać projekt, a następnie diagram.

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

## <a name="alternative-methods"></a>Metody alternatywne
 W przypadku wielu aplikacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus umożliwia odwoływanie się do modeli i elementów w obrębie nich oraz zapewnia lepszą niezawodność i elastyczność niż w przypadku metod opisanych w tym temacie. Zapewnia standardową metodę tworzenia linków między dowolnymi elementami, w tych samych lub różnych modelach. Aby uzyskać więcej informacji, zobacz [integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Można również otworzyć modele i diagramy w interfejsie użytkownika przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu API. Aby uzyskać więcej informacji, zobacz [otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="stand-alone-applications"></a><a name="Standalone"></a> Aplikacje autonomiczne
 Przykład w poprzedniej sekcji będzie działał w rozszerzeniach programu Visual Studio. Istnieje możliwość odczytywania modelu w aplikacji autonomicznej, ale należy dodać do projektu pewne odwołania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

> [!NOTE]
> Szczegóły dotyczące sposobu odczytu modelu w aplikacji autonomicznej mogą ulec zmianie w przyszłych wersjach produktu. Niektóre funkcje, które są dostępne w bieżącej wersji, mogą nie być dostępne w przyszłych wersjach.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Aby dodać odwołania do odczytu modelu w aplikacji autonomicznej.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, w którym tworzysz aplikację, a następnie kliknij polecenie **Właściwości**. W edytorze właściwości na karcie **aplikacja** Ustaw **platformę docelową** na wymaganą wersję .NET Framework.

2. Dodaj [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] odwołania potrzebne do uzyskiwania dostępu do modeli UML, zazwyczaj:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Oprócz odwołań wymienionych w poprzednich sekcjach Dodaj następujące odwołania do projektu z **folderu \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies**:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Jeśli chcesz czytać diagramy w aplikacji, możesz również wymagać następujących odwołań:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Zobacz też
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md) — tworzenie [modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
