---
title: 'Instrukcje: Odwołanie do nazwy lub lokalizacji pliku projektu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a5d07c374e75bd7f042f466f13fc5727241e252
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54781005"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Instrukcje: Odwołanie do nazwy lub lokalizacji pliku projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W pliku projektu bez konieczności tworzenia własnych właściwości, można użyć nazwy lub lokalizacji projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Udostępnia właściwości zastrzeżonych, które odwołują się nazwa pliku projektu i inne właściwości związane z tym projektem. Aby uzyskać więcej informacji na temat właściwości zastrzeżonych, zobacz [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Za pomocą MSBuildProjectName właściwość  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera niektóre właściwości zastrzeżonych, których można użyć w plikach projektu bez definiowania ich za każdym razem. Na przykład właściwości zastrzeżonych `MSBuildProjectName` zawiera odwołanie do nazwy pliku projektu.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Aby użyć MSBuildProjectName właściwość  
  
- Odwoływać się do właściwości w pliku projektu przy użyciu notacji $ (), tak samo jak dowolnej właściwości. Na przykład:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Zaletą używania zastrzeżonych właściwości to, że wszelkie zmiany nazwy pliku projektu są włączane automatycznie. Przy następnym uruchomieniu, skompiluj projekt, plik wyjściowy będzie zawierał nową nazwę z żadnych dodatkowych czynności ze strony użytkownika.  
  
> [!NOTE]
>  Właściwości zastrzeżone nie mogą zostać redefiniowane w pliku projektu.  
  
## <a name="example"></a>Przykład  
 Następujący przykład pliku projektu odwołuje się do nazwy projektu jako zarezerwowane właściwości w celu określenia nazwy dla danych wyjściowych.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
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
  
## <a name="see-also"></a>Zobacz też  
[MSBuild](msbuild.md)  
 [Właściwości MSBuild zarezerwowane i dobrze znane](../msbuild/msbuild-reserved-and-well-known-properties.md)
