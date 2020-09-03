---
title: ParallelCustomBuild — zadanie | Microsoft Docs
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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77279261"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild, zadanie

Uruchamianie równoległych wystąpień [zadania CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **ParallelCustomBuild** .

|Parametr|Opis|
|---------------|-----------------|
|**BreakOnFirstFailure**|Opcjonalny parametr **bool** .|
|**MaxItemsInBatch**|Opcjonalny parametr **int** .|
|**MaxProcesses**|Opcjonalny parametr **int** .|
|**Źródła**|Wymagany parametr **ITaskItem []** .|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)