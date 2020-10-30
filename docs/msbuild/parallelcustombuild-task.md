---
title: ParallelCustomBuild — zadanie | Microsoft Docs
description: Dowiedz się, jak MSBuild używa zadania ParallelCustomBuild do uruchamiania równoległych wystąpień zadania CustomBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048892"
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
|**Źródeł**|Wymagany parametr **ITaskItem []** .|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)