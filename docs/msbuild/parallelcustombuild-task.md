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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963757"
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