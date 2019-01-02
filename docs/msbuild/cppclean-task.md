---
title: Cppclean — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbf575db0289f0b5bbb5fbcd0bf47605871e52c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966375"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie
Usuwa pliki tymczasowe, utworzone przez program MSBuild podczas kompilowania projektu Visual C++. Proces usuwania plików kompilacji jest znany jako *czyszczenia*.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **cppclean —** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**DeletedFiles**|Opcjonalnie `ITaskItem[]` parametr wyjściowy.<br /><br /> Określa tablicę elementów MSBuild dane wyjściowe pliku, które może być używany i wyemitowane przez zadania.|  
|**DoDelete**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`czyszczenie tymczasowej pliki kompilacji.|  
|**FilePatternsToDeleteOnClean**|Wymagane `String` parametru.<br /><br /> Określa rozdzielaną średnikami listę rozszerzeń plików, aby wyczyścić.|  
|**FilesExcludedFromClean**|Opcjonalnie `String` parametru.<br /><br /> Określa rozdzielaną średnikami listę plików nie można wyczyścić.|  
|**FoldersToClean**|Wymagane `String` parametru.<br /><br /> Określa rozdzielaną średnikami listę katalogów do czyszczenia. Można określić pełną lub względną ścieżkę i ścieżki mogą zawierać symbol wieloznaczny (*).|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)