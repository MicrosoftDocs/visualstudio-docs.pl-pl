---
title: GetOutOfDateItems — zadanie | Microsoft Docs
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
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747317"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems, zadanie

Zadanie pomocnika, które odczytuje stare tlogs, zapisuje nowe tlogs i zwraca zestaw elementów, które nie są aktualne.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **GetOutOfDateItems** .

|Parametr|Opis|
|---------------|-----------------|
|**CheckForInterdependencies**|Opcjonalny parametr **bool** .|
|**CommandMetadataName**|Opcjonalny parametr **ciągu** .|
|**DependenciesMetadataName**|Opcjonalny parametr **ciągu** .|
|**HasInterdependencies**|Opcjonalny parametr wyjściowy **bool** .|
|**OutOfDateSources**|Opcjonalny parametr wyjściowy **ITaskItem []** .|
|**OutputsMetadataName**|Wymagany parametr **ciągu** .|
|**Źródeł**|Opcjonalny parametr **ITaskItem []** .|
|**TLogDirectory**|Wymagany parametr **ciągu** .|
|**TLogNamePrefix**|Wymagany parametr **ciągu** .|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)