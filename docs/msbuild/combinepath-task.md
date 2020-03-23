---
title: Zadanie CombinePath | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634438"
---
# <a name="combinepath-task"></a>CombinePath — zadanie

Łączy określone ścieżki w jedną ścieżkę.
## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry [zadania CombinePath](../msbuild/combinepath-task.md).


|Parametr|Opis|
|---------------|-----------------|
|`BasePath`|Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka podstawowa do łączenia z innymi ścieżkami. Może być ścieżką względną, ścieżką bezwzględną lub pustą.|
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do połączenia z BasePath w celu utworzenia połączonej ścieżki. Ścieżki mogą być względne lub bezwzględne.|
|`CombinedPaths`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Połączona ścieżka, która jest tworzona przez to zadanie.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
