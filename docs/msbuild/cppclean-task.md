---
title: CPPClean — — zadanie | Microsoft Docs
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
ms.openlocfilehash: 827014e04c23239274e31b994fd0178cbe8e5883
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596076"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie
Usuwa pliki tymczasowe, które program MSBuild tworzy po C++ skompilowaniu projektu. Proces usuwania plików kompilacji jest znany jako *czyszczenie*.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **CPPClean —** .

|Parametr|Opis|
|---------------|-----------------|
|**DeletedFiles**|Opcjonalny `ITaskItem[]` parametr wyjściowy.<br /><br /> Definiuje tablicę elementów plików wyjściowych programu MSBuild, które mogą być używane i emitowane przez zadania.|
|**DoDelete**|Opcjonalny parametr **logiczny** .<br /><br /> W przypadku `true`Wyczyść pliki tymczasowej kompilacji.|
|**FilePatternsToDeleteOnClean**|Wymagany `String` parametr.<br /><br /> Określa rozdzielaną średnikami listę rozszerzeń plików, które mają zostać oczyszczone.|
|**FilesExcludedFromClean**|Opcjonalny parametr `String`.<br /><br /> Określa rozdzielaną średnikami listę plików, które nie są czyste.|
|**FoldersToClean**|Wymagany `String` parametr.<br /><br /> Określa rozdzielaną średnikami listę katalogów do oczyszczenia. Można określić pełną lub względną ścieżkę, a ścieżka może zawierać symbol wieloznaczny (*).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
