---
title: GetFrameworkPath — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149487"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestawów.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GetFrameworkPath` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 1,1, jeśli istnieją. W przeciwnym razie zwraca `null` .|  
|`FrameworkVersion20Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 2,0, jeśli istnieją. W przeciwnym razie zwraca `null` .|  
|`FrameworkVersion30Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,0, jeśli istnieją. W przeciwnym razie zwraca `null` .|  
|`FrameworkVersion35Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,5, jeśli istnieją. W przeciwnym razie zwraca `null` .|  
|`FrameworkVersion40Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 4,0, jeśli istnieją. W przeciwnym razie zwraca `null` .|  
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszych zestawów struktury, jeśli są dostępne. W przeciwnym razie zwraca `null` .|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku zainstalowania kilku wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zadanie to zwraca wersję, która [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] została zaprojektowana do uruchamiania programu.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `GetFrameworkPath` zadania do przechowywania ścieżki do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `FrameworkPath` właściwości.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
