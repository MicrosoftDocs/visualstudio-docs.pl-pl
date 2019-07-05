---
title: Zadanie CustomBuild | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587015"
---
# <a name="custombuild-task"></a>Zadanie CustomBuild

Narzędzia kompilatora Visual C++, jest zawijany cmd.exe. Ta klasa jest pochodną [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nie używa pliku śledzenia odnajdywania zależnościach plików. Wszystkie zależności powinien być jawnie określony jako AdditionalDependencies dla kompilacji przyrostowej działa prawidłowo.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **CustomBuild** zadania.

|Parametr|Opis|
|---------------|-----------------|
|**BuildSuffix**|Opcjonalnie **ciąg** parametru.|
|**Źródła**|Wymagane **[] ITaskItem** parametru.|
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
