---
title: CustomBuild — zadanie | Microsoft Docs
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595348"
---
# <a name="custombuild-task"></a>CustomBuild, zadanie

Zawija narzędzie kompilatora firmy C++ Microsoft, cmd. exe. Ta klasa pochodzi z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nie używa śledzenia plików do odnajdywania zależności pliku. Wszystkie zależności należy jawnie określić jako AdditionalDependencies, aby kompilacja przyrostowa działała prawidłowo.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **CustomBuild** .

|Parametr|Opis|
|---------------|-----------------|
|**BuildSuffix**|Opcjonalny parametr **ciągu** .|
|**Źródeł**|Wymagany parametr **ITaskItem []** .|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
