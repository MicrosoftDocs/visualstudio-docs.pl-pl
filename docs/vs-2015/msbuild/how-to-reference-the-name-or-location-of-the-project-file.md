---
title: 'Instrukcje: odwoływanie się do nazwy lub lokalizacji pliku projektu | Microsoft Docs'
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
ms.openlocfilehash: eae8a32d4587b71f238c023d08a1328ce83ba37d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818197"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Porady: odwołanie do nazwy lub lokalizacji pliku projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć nazwy lub lokalizacji projektu w samym pliku projektu bez konieczności tworzenia własnej właściwości. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera zastrzeżone właściwości, które odwołują się do nazwy pliku projektu i innych właściwości związanych z projektem. Aby uzyskać więcej informacji na temat właściwości zastrzeżonych, zobacz [Właściwości zarezerwowane i dobrze znane programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Używanie właściwości MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] udostępnia pewne właściwości zastrzeżone, których można użyć w plikach projektu bez definiowania ich za każdym razem. Na przykład Właściwość zastrzeżone `MSBuildProjectName` zawiera odwołanie do nazwy pliku projektu.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Aby użyć właściwości MSBuildProjectName  
  
- Odwoływanie się do właściwości w pliku projektu za pomocą notacji $ (), tak jak w przypadku każdej właściwości. Na przykład:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Zaletą użycia zastrzeżonej właściwości jest to, że wszelkie zmiany nazwy pliku projektu są włączane automatycznie. Przy następnym kompilowaniu projektu plik wyjściowy będzie miał nową nazwę, która nie wymaga żadnych dalszych akcji.  
  
> [!NOTE]
> W pliku projektu nie można ponownie zdefiniować zarezerwowanych właściwości.  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy plik projektu odwołuje się do nazwy projektu jako zastrzeżonej właściwości, aby określić nazwę danych wyjściowych.  
  
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
 [Właściwości zarezerwowane i dobrze znane dla programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
