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
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634347"
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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
