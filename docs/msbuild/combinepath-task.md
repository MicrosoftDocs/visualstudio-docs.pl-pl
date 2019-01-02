---
title: Combinepath — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 542efb2cb1de44da95f640efbc316dc2cf373212
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966498"
---
# <a name="combinepath-task"></a>CombinePath — zadanie
Łączy określonych ścieżek w pojedynczą ścieżkę.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry [combinepath — zadanie](../msbuild/combinepath-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BasePath`|Wymagane `String` parametru.<br /><br /> Ścieżki podstawowej, aby połączyć się z innych ścieżek. Może być ścieżką względną, ścieżka bezwzględna lub pusty.|  
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do łączenia z BasePath do utworzenia złożonej ścieżki. Ścieżki mogą być względna lub bezwzględna.|  
|`CombinedPaths`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Połączone ścieżki, który jest tworzony przez to zadanie.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)