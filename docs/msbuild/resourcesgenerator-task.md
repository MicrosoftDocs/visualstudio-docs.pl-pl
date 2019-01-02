---
title: Resourcesgenerator — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c28327ec391bbed7062d5957739f21d27655b048
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882712"
---
# <a name="resourcesgenerator-task"></a>Resourcesgenerator — zadanie
<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> Zadań osadza co najmniej jeden zasób (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w formacie binarnym, a inne typy rozszerzeń) do *Resources* pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do katalogu wyjściowego. Jeśli ścieżka nie jest ścieżką bezwzględną, jest ona traktowana jako ścieżkę, która jest określana względem katalogu głównego projektu.|  
|`OutputResourcesFile`|Wymagane **[] ITaskItem** parametr wyjściowy.<br /><br /> Określa ścieżkę i nazwę wygenerowany *Resources* pliku. Jeśli ścieżka nie jest ścieżką bezwzględną *Resources* wygenerowaniu pliku względem katalogu głównego projektu.|  
|`ResourcesFiles`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa co najmniej jeden zasób do osadzenia w wygenerowanym *Resources* pliku.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje *Resources* plików za pomocą jednego *.bmp* zasobów. *.Bmp* zasobów jest generowana do katalogu, który jest określana względem katalogu głównego projektu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)