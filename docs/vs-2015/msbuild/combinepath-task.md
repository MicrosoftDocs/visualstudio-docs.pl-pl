---
title: CombinePath — — zadanie | Microsoft Docs
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160385"
---
# <a name="combinepath-task"></a>CombinePath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Łączy określone ścieżki w jedną ścieżkę.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry [zadania CombinePath —](../msbuild/combinepath-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BasePath`|Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka podstawowa, która ma zostać połączona z innymi ścieżkami. Może być ścieżką względną, ścieżką bezwzględną lub pustą.|  
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do połączenia z BasePath w celu utworzenia połączonej ścieżki. Ścieżki mogą być względne lub bezwzględne.|  
|`CombinedPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Połączona Ścieżka utworzona przez to zadanie.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
