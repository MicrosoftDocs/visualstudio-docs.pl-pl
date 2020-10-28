---
title: CustomBuild — zadanie | Microsoft Docs
description: W tym artykule opisano zadanie MSBuild CustomBuild, które jest używane przez program MSBuild do obsługi dostosowywania procesu kompilacji C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796553"
---
# <a name="custombuild-task"></a>CustomBuild, zadanie

Zawija narzędzie kompilatora języka Microsoft C++ cmd.exe. Ta klasa pochodzi z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nie używa śledzenia plików do odnajdywania zależności pliku. Wszystkie zależności należy jawnie określić jako AdditionalDependencies, aby kompilacja przyrostowa działała prawidłowo.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **CustomBuild** .

|Parametr|Opis|
|---------------|-----------------|
|**BuildSuffix**|Opcjonalny parametr **ciągu** .|
|**Źródeł**|Wymagany parametr **ITaskItem []** .|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .|

## <a name="see-also"></a>Zobacz także

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
