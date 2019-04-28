---
title: Zadanie GetOutOfDateItems | Dokumentacja firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977493"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems task

Zadanie pomocnika, które odczytuje tlogs stare, zapisuje nowe tlogs i zwraca zestaw elementów, które nie są aktualne.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **GetOutOfDateItems** zadania.

|Parametr|Opis|
|---------------|-----------------|
|**CheckForInterdependencies**|Opcjonalnie **bool** parametru.|
|**CommandMetadataName**|Opcjonalnie **ciąg** parametru.|
|**DependenciesMetadataName**|Opcjonalnie **ciąg** parametru.|
|**HasInterdependencies**|Opcjonalnie **bool** parametr wyjściowy.|
|**OutOfDateSources**|Opcjonalnie **[] ITaskItem** parametr wyjściowy.|
|**OutputsMetadataName**|Wymagane **ciąg** parametru.|
|**Źródła**|Opcjonalnie **[] ITaskItem** parametru.|
|**TLogDirectory**|Wymagane **ciąg** parametru.|
|**TLogNamePrefix**|Wymagane **ciąg** parametru.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)