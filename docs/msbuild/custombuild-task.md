---
title: Zadanie CustomBuild | Dokumenty firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595348"
---
# <a name="custombuild-task"></a>Zadanie CustomBuild

Zawija narzędzie kompilatora Microsoft C++, cmd.exe. Ta klasa pochodzi z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nie używa śledzenia plików do odnajdywać zależności plików. Wszystkie zależności powinny być jawnie określone jako AdditionalDependencies dla kompilacji przyrostowej działa poprawnie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **CustomBuild.**

|Parametr|Opis|
|---------------|-----------------|
|**Tworzy przyrostek**|Opcjonalny parametr **ciągu.**|
|**Źródeł**|Wymagany parametr **ITaskItem[].**|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **ciągu.**|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
