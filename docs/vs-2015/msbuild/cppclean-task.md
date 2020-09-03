---
title: CPPClean — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196573"
---
# <a name="cppclean-task"></a>CPPClean — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usuwa pliki tymczasowe, które program MSBuild tworzy po skompilowaniu projektu Visual C++. Proces usuwania plików kompilacji jest znany jako *czyszczenie*.  

## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **CPPClean —** .  

|            Parametr            |                                                                                                Opis                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Opcjonalny `ITaskItem[]` parametr wyjściowy.<br /><br /> Definiuje tablicę elementów plików wyjściowych programu MSBuild, które mogą być używane i emitowane przez zadania.                                |
|          **DoDelete**           |                                                            Opcjonalny parametr **logiczny** .<br /><br /> `true`Wyczyść pliki tymczasowej kompilacji.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę rozszerzeń plików, które mają zostać oczyszczone.                                             |
|   **FilesExcludedFromClean**    |                                                    Opcjonalny `String` parametr.<br /><br /> Określa rozdzielaną średnikami listę plików, które nie są czyste.                                                    |
|       **FoldersToClean**        | Wymagany parametr interfejsu `String`.<br /><br /> Określa rozdzielaną średnikami listę katalogów do oczyszczenia. Można określić pełną lub względną ścieżkę, a ścieżka może zawierać symbol wieloznaczny ( **\\** \* ). |

## <a name="remarks"></a>Uwagi  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
