---
title: Zadanie ParallelCustomBuild | Dokumentacja firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 506ead6680bd9a0aaaf38d6959da02a14dfee337
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58071133"
---
# <a name="parallelcustombuild-task"></a>Zadanie ParallelCustomBuild

Uruchamianie równoległych wystąpień [zadań CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **ParallelCustomBuild** zadania.

|Parametr|Opis|
|---------------|-----------------|
|**BreakOnFirstFailure**|Opcjonalnie **bool** parametru.|
|**MaxItemsInBatch**|Opcjonalnie **int** parametru.|
|**MaxProcesses**|Opcjonalnie **int** parametru.|
|**Źródła**|Wymagane **[] ITaskItem** parametru.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)