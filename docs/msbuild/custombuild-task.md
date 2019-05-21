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
ms.openlocfilehash: 6d466dec85a0bdf242120ef5e88a0d5f5d2ac48e
ms.sourcegitcommit: 0ef51e3517436a85cfb85bf492722d566ce602c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934516"
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
