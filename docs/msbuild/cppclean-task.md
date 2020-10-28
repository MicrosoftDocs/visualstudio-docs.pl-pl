---
title: CPPClean — — zadanie | Microsoft Docs
description: W tym artykule opisano zadanie CPPClean —, które służy do usuwania plików tymczasowych tworzonych przez program MSBuild po skompilowaniu projektu języka C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8f59b66ab1fc117a29d7ed8db2d380b4b11b437
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796111"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie

Usuwa pliki tymczasowe, które program MSBuild tworzy po skompilowaniu projektu języka C++. Proces usuwania plików kompilacji jest znany jako *czyszczenie* .

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **CPPClean —** .

|Parametr|Opis|
|---------------|-----------------|
|**DeletedFiles**|Opcjonalny `ITaskItem[]` parametr wyjściowy.<br /><br /> Definiuje tablicę elementów plików wyjściowych programu MSBuild, które mogą być używane i emitowane przez zadania.|
|**DoDelete**|Opcjonalny parametr **logiczny** .<br /><br /> `true`Wyczyść pliki tymczasowej kompilacji.|
|**FilePatternsToDeleteOnClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę rozszerzeń plików, które mają zostać oczyszczone.|
|**FilesExcludedFromClean**|Opcjonalny `String` parametr.<br /><br /> Określa rozdzielaną średnikami listę plików, które nie są czyste.|
|**FoldersToClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę katalogów do oczyszczenia. Można określić pełną lub względną ścieżkę, a ścieżka może zawierać symbol wieloznaczny (*).|

## <a name="see-also"></a>Zobacz także

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
