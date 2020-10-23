---
title: GetOutOfDateItems — zadanie | Microsoft Docs
description: Za pomocą zadania pomocnika programu MSBuild GetOutOfDateItems można odczytywać i zapisywać dzienniki transakcji (TLOGs) oraz zwracać zestawy elementów, które nie są aktualne.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436824"
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

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)