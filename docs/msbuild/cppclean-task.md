---
title: CPPClean Zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634347"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie

Usuwa pliki tymczasowe, które MSBuild tworzy podczas tworzenia projektu C++. Proces usuwania plików kompilacji jest znany jako *czyszczenie*.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **CPPClean.**

|Parametr|Opis|
|---------------|-----------------|
|**Pliki usunięte**|Opcjonalny parametr wyjściowy. `ITaskItem[]`<br /><br /> Definiuje tablicę elementów pliku wyjściowego MSBuild, które mogą być używane i emitowane przez zadania.|
|**DoDelete (DoDelete)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`, czyść pliki kompilacji tymczasowej.|
|**FilePatternsToDeleteOnClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa listę rozdzielanych średnikami rozszerzeń plików do czyszczenia.|
|**PlikiExcludedFromClean**|Parametr `String` opcjonalny.<br /><br /> Określa listę plików rozdzielanych średnikami, które mają nie być czyszczone.|
|**FoldersToClean**|Wymagany parametr interfejsu `String`.<br /><br /> Określa listę katalogów rozdzielanych średnikami do czyszczenia. Można określić pełną lub względną ścieżkę, a ścieżka może zawierać symbol symbolu wieloznacznego (*).|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
