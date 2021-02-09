---
title: Zadania programu MSBuild specyficzne dla języka C++ | Microsoft Docs
description: Zobacz zadania programu MSBuild, które są dostępne po zainstalowaniu języka C++, których MSBuild używa podczas kompilowania kodu w języku C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 82ba5ad3beb8a676df23cc69184c8766bca72f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878269"
---
# <a name="msbuild-tasks-specific-to-c"></a>Zadania programu MSBuild specyficzne dla języka C++

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Po zainstalowaniu języka C++ dostępne są następujące zadania, oprócz tych, które są instalowane z programem MSBuild. Aby uzyskać więcej informacji, zobacz [MSBuild (C++) — Omówienie](/cpp/build/msbuild-visual-cpp-overview).

 Oprócz parametrów dla każdego zadania, każde zadanie ma również następujące parametry.

| Parametr | Opis |
|-------------------| - |
| `Condition` | Opcjonalny `String` parametr.<br /><br /> `Boolean`Wyrażenie używane przez aparat MSBuild do określenia, czy zadanie zostanie wykonane. Aby uzyskać informacje o warunkach, które są obsługiwane przez program MSBuild, zobacz [warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.<br /><br /> Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[BscMake, zadanie](../msbuild/bscmake-task.md)|Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (*bscmake.exe*).|
|[CL — Zadanie](../msbuild/cl-task.md)|Zawija narzędzie kompilatora języka C++ (*cl.exe*).|
|[CPPClean, zadanie](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, które program MSBuild tworzy po skompilowaniu projektu języka C++.|
|[ClangCompile, zadanie](../msbuild/clangcompile-task.md)|Zawija narzędzie kompilatora języka C++ (*clang.exe*).|
|[CustomBuild, zadanie](../msbuild/custombuild-task.md)|Zawija narzędzie kompilatora języka C++ (*cmd.exe*).|
|[FXC, zadanie](../msbuild/fxc-task.md)|Użyj kompilatorów modułu cieniującego HLSL w procesie kompilacji.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Odczytuje stare tlogs, zapisuje nowe tlogs i zwraca zestaw elementów, które nie są aktualne. (zadanie pomocnika)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Pobiera nazwę pliku wyjściowego dla CL i innych narzędzi, które umożliwiają określenie tylko katalogu wyjściowego lub pełną nazwę pliku lub Nothing. (zadanie pomocnika)|
|[LIB — Zadanie](../msbuild/lib-task.md)|Zawija narzędzie Microsoft 32-bit Library Manager (*lib.exe*).|
|[Link — Zadanie](../msbuild/link-task.md)|Zawija narzędzie konsolidatora C++ (*link.exe*).|
|[MIDL — Zadanie](../msbuild/midl-task.md)|Zawija Microsoft Interface Definition Language (*midl.exe*) narzędzie kompilatora (MIDL).|
|[MT — Zadanie](../msbuild/mt-task.md)|Zawija narzędzie manifestu firmy Microsoft (*mt.exe*).|
|[MultiToolTask, zadanie](../msbuild/multitooltask-task.md)|Brak opisu.|
|[ParallelCustomBuild, zadanie](../msbuild/parallelcustombuild-task.md)|Uruchamianie równoległych wystąpień [zadania CustomBuild](../msbuild/custombuild-task.md).|
|[RC — Zadanie](../msbuild/rc-task.md)|Zawija narzędzie kompilatora zasobów systemu Microsoft Windows (*rc.exe*).|
|[SetEnv, zadanie](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość określonej zmiennej środowiskowej.|
|[TrackedVCToolTask, klasa podstawowa](../msbuild/trackedvctooltask-base-class.md)|Dziedziczy po [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage — Zadanie](../msbuild/vcmessage-task.md)|Rejestruje komunikaty ostrzegawcze i komunikaty o błędach podczas kompilacji. (Nierozszerzalny. Tylko do użytku wewnętrznego.)|
|[VCToolTask, klasa podstawowa](../msbuild/vctooltask-base-class.md)|Dziedziczy po [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake — Zadanie](../msbuild/xdcmake-task.md)|Zawija narzędzie dokumentacji XML (*xdcmake.exe*), które scala pliki komentarzy dokumentów XML (*. xdc*) w pliku *XML* .|
|[XSD — Zadanie](../msbuild/xsd-task.md)|Zawija narzędzie definicji schematu XML (*xsd.exe*), które generuje pliki schematu lub klasy ze źródła. *Zobacz uwagę poniżej.*|
|[Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)|Opisuje elementy systemu MSBuild.|
|[Zadania](../msbuild/msbuild-tasks.md)|Opisuje zadania, które są jednostkami kodu, które można połączyć w celu utworzenia kompilacji.|
|[Pisanie zadań](../msbuild/task-writing.md)|Opisuje sposób tworzenia zadania.|

> [!NOTE]
> Począwszy od programu Visual Studio 2017, obsługa projektu C++ dla *xsd.exe* jest przestarzała. Można nadal używać interfejsów API **Microsoft. VisualC. CppCodeProvider** , ręcznie dodając *CppCodeProvider.dll* do pamięci podręcznej GAC.
