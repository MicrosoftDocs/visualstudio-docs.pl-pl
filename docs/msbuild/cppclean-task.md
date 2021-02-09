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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901436"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie

Usuwa pliki tymczasowe, które program MSBuild tworzy po skompilowaniu projektu języka C++. Proces usuwania plików kompilacji jest znany jako *czyszczenie*.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **CPPClean —** .

|Parametr|Opis|
|---------------|-----------------|
|**DeletedFiles**|Opcjonalny `ITaskItem[]` parametr wyjściowy.<br /><br /> Definiuje tablicę elementów plików wyjściowych programu MSBuild, które mogą być używane i emitowane przez zadania.|
|**DoDelete**|Opcjonalny parametr **logiczny** .<br /><br /> `true`Wyczyść pliki tymczasowej kompilacji.|
|**FilePatternsToDeleteOnClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę rozszerzeń plików, które mają zostać oczyszczone.|
|**FilesExcludedFromClean**|Opcjonalny `String` parametr.<br /><br /> Określa rozdzielaną średnikami listę plików, które nie są czyste.|
|**FoldersToClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę katalogów do oczyszczenia. Można określić pełną lub względną ścieżkę, a ścieżka może zawierać symbol wieloznaczny (*).|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
