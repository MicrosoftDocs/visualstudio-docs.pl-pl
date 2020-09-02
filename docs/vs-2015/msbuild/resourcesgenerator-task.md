---
title: ResourcesGenerator — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa8b438727160bb5a752643f7ef9791ca5e09245
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682139"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>Zadanie osadza jeden lub więcej zasobów (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym i innych typów rozszerzenia) w pliku Resources.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPath`|Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę katalogu wyjściowego. Jeśli ścieżka nie jest ścieżką bezwzględną, jest traktowana jako ścieżka względem katalogu głównego projektu.|  
|`OutputResourcesFile`|Wymagany parametr wyjściowy **ITaskItem []** .<br /><br /> Określa ścieżkę i nazwę wygenerowanego pliku Resources. Jeśli ścieżka nie jest ścieżką bezwzględną, plik Resources jest generowany względem katalogu głównego projektu.|  
|`ResourcesFiles`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa co najmniej jeden zasób do osadzenia w wygenerowanym pliku Resources.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje plik resources z pojedynczym zasobem. bmp. Zasób. bmp jest generowany do katalogu, który jest względny dla katalogu głównego projektu.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
