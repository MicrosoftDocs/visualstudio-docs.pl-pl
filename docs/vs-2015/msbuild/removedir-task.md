---
title: RemoveDir — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70bd6623d86ecfa76d3e09de09a8dcfad3d5da20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159255"
---
# <a name="removedir-task"></a>RemoveDir — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usuwa określone katalogi i wszystkie jego pliki i podkatalogi.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RemoveDir` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Directories`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa katalogi do usunięcia.|  
|`RemovedDirectories`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera katalogi, które zostały pomyślnie usunięte.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa katalogi określone przez `OutputDirectory` `DebugDirectory` właściwości i. Te ścieżki są traktowane jako względne dla katalogu projektu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
        <DebugDirectory>\Debug\</DebugDirectory>  
    </PropertyGroup>  
  
    <Target Name="RemoveDirectories">  
        <RemoveDir  
            Directories="$(OutputDirectory);$(DebugDirectory)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
