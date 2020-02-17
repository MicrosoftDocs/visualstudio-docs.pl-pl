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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272395"
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

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)