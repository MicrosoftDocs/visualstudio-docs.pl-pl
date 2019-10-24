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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748110"
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
