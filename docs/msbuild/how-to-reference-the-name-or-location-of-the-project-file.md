---
title: 'Instrukcje: Odwołanie do nazwy lub lokalizacji pliku projektu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ce03be9eb9d1fa4926eb1100f9a2aad5612a61d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906036"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Instrukcje: Odwołanie do nazwy lub lokalizacji pliku projektu
W pliku projektu bez konieczności tworzenia własnych właściwości, można użyć nazwy lub lokalizacji projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Udostępnia właściwości zastrzeżonych, które odwołują się nazwa pliku projektu i inne właściwości związane z tym projektem. Aby uzyskać więcej informacji na temat właściwości zastrzeżonych, zobacz [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="use-the-project-properties"></a>Korzystanie z właściwości projektu
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zawiera niektóre właściwości zastrzeżonych, których można użyć w plikach projektu bez definiowania ich za każdym razem. Na przykład właściwości zastrzeżonych `MSBuildProjectName` zawiera odwołanie do nazwy pliku projektu. Właściwości zastrzeżone `MSBuildProjectDirectory` zawiera odwołanie do lokalizacji pliku projektu.
  
#### <a name="to-use-the-project-properties"></a>Aby użyć właściwości projektu
  
- Odwoływać się do właściwości w pliku projektu przy użyciu notacji $ (), tak samo jak dowolnej właściwości. Na przykład:  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  Zaletą używania zastrzeżonych właściwości to, że wszelkie zmiany nazwy pliku projektu są włączane automatycznie. Przy następnym uruchomieniu, skompiluj projekt, plik wyjściowy będzie zawierał nową nazwę z żadnych dodatkowych czynności ze strony użytkownika.  
  
> [!NOTE]
>  Właściwości zastrzeżone nie mogą zostać redefiniowane w pliku projektu.  
  
## <a name="example"></a>Przykład  
 Następujący przykład pliku projektu odwołuje się do nazwy projektu jako zarezerwowane właściwości w celu określenia nazwy dla danych wyjściowych.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
     </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>Przykład
 Poniższy przykładowy plik projektu używa `MSBuildProjectDirectory` zastrzeżone właściwości, aby utworzyć pełną ścieżkę do pliku w lokalizacji pliku projektu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz także  
[MSBuild](../msbuild/msbuild.md)  
[Program MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)
