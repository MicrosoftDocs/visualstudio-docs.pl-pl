---
title: CombinePath — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 533f87eba9032efa7dc60ac682bbe400cb640727
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634438"
---
# <a name="combinepath-task"></a>CombinePath — zadanie

Łączy określone ścieżki w jedną ścieżkę.
## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry [zadania CombinePath —](../msbuild/combinepath-task.md).


|Parametr|Opis|
|---------------|-----------------|
|`BasePath`|Wymagany `String` parametr.<br /><br /> Ścieżka podstawowa, która ma zostać połączona z innymi ścieżkami. Może być ścieżką względną, ścieżką bezwzględną lub pustą.|
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do połączenia z BasePath w celu utworzenia połączonej ścieżki. Ścieżki mogą być względne lub bezwzględne.|
|`CombinedPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Połączona Ścieżka utworzona przez to zadanie.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
