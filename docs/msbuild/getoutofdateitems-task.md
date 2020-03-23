---
title: GetOutOfDateItems Zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272395"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems zadanie

Zadanie pomocnika, które odczytuje stare tlogi, zapisuje nowe tlogi i zwraca zestaw elementów, które nie są aktualne.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **GetOutOfDateItems.**

|Parametr|Opis|
|---------------|-----------------|
|**CheckForInterdependencies**|Opcjonalny parametr **bool.**|
|**Nazwami commandmetadata**|Opcjonalny parametr **ciągu.**|
|**Nazwami zależnościMetadataName**|Opcjonalny parametr **ciągu.**|
|**HasInterdependencies**|Opcjonalny parametr wyjściowy **bool.**|
|**OutOfDateŹródła**|Opcjonalny parametr **wyjściowy ITaskItem[].**|
|**Nazwa danych Wyjściowych**|Wymagany parametr **ciągu.**|
|**Źródeł**|Opcjonalny parametr **ITaskItem[].**|
|**TLogDirectory (TLogDirectory)**|Wymagany parametr **ciągu.**|
|**Poprawka TLogNamePrefix**|Wymagany parametr **ciągu.**|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)