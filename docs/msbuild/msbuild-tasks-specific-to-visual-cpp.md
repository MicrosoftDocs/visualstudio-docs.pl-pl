---
title: Zadania programu MSBuild specyficzne C++ dla | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d6ea400d7473fae27ac4b17d9e3692748db549f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748072"
---
# <a name="msbuild-tasks-specific-to-c"></a>Zadania programu MSBuild specyficzne dlaC++
Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Po C++ zainstalowaniu programu oprócz tych, które są instalowane z programem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], dostępne są następujące zadania. Aby uzyskać więcej informacji, zobacz [MSBuildC++() — Omówienie](/cpp/build/msbuild-visual-cpp-overview).

 Oprócz parametrów dla każdego zadania, każde zadanie ma również następujące parametry.

| Parametr | Opis |
|-------------------| - |
| `Condition` | Opcjonalny parametr `String`.<br /><br /> Wyrażenie `Boolean` używane przez aparat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do określenia, czy zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Opcjonalny parametr. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w elemencie `Target` i kompilacja nadal będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Gdy zadanie nie powiedzie się, pozostałe zadania w elemencie `Target` i kompilacja nie są wykonywane, a cały element `Target` i kompilacja są uznawane za niepowodzenie.<br /><br /> Wersje .NET Framework przed 4,5 są obsługiwane tylko przez wartości `true` i `false`.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[BscMake, zadanie](../msbuild/bscmake-task.md)|Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (*BSCMAKE. exe*).|
|[CL — zadanie](../msbuild/cl-task.md)|Zawija narzędzie C++ kompilatora (*CL. exe*).|
|[CPPClean —, zadanie](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, które program MSBuild tworzy po C++ skompilowaniu projektu.|
|[ClangCompile, zadanie](../msbuild/clangcompile-task.md)|Zawija narzędzie C++ kompilatora (*Clang. exe*).|
|[CustomBuild, zadanie](../msbuild/custombuild-task.md)|Zawija narzędzie C++ kompilatora (*cmd. exe*).|
|[FXC, zadanie](../msbuild/fxc-task.md)|Użyj kompilatorów modułu cieniującego HLSL w procesie kompilacji.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Odczytuje stare tlogs, zapisuje nowe tlogs i zwraca zestaw elementów, które nie są aktualne. (zadanie pomocnika)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Pobiera nazwę pliku wyjściowego dla CL i innych narzędzi, które umożliwiają określenie tylko katalogu wyjściowego lub pełną nazwę pliku lub Nothing. (zadanie pomocnika)|
|[LIB — zadanie](../msbuild/lib-task.md)|Zawija narzędzie Microsoft 32-bit Library Manager (*lib. exe*).|
|[Połącz zadanie](../msbuild/link-task.md)|Zawija narzędzie C++ konsolidatora (*link. exe*).|
|[MIDL, zadanie](../msbuild/midl-task.md)|Zawija narzędzie kompilatora Microsoft Interface Definition Language (MIDL) (*MIDL. exe*).|
|[MT — zadanie](../msbuild/mt-task.md)|Zawija narzędzie manifestu Microsoft (*Mt. exe*).|
|[MultiToolTask, zadanie](../msbuild/multitooltask-task.md)|Brak opisu.|
|[ParallelCustomBuild, zadanie](../msbuild/parallelcustombuild-task.md)|Uruchamianie równoległych wystąpień [zadania CustomBuild](../msbuild/custombuild-task.md).|
|[RC — zadanie](../msbuild/rc-task.md)|Zawija narzędzie kompilatora zasobów systemu Microsoft Windows (*RC. exe*).|
|[SetEnv, zadanie](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość określonej zmiennej środowiskowej.|
|[Klasa bazowa TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Dziedziczy po [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage —, zadanie](../msbuild/vcmessage-task.md)|Rejestruje komunikaty ostrzegawcze i komunikaty o błędach podczas kompilacji. (Nierozszerzalny. Tylko do użytku wewnętrznego.)|
|[Klasa bazowa VCToolTask](../msbuild/vctooltask-base-class.md)|Dziedziczy po [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake, zadanie](../msbuild/xdcmake-task.md)|Zawija narzędzie dokumentacji XML (*xdcmake. exe*), które scala pliki komentarzy dokumentów XML ( *. xdc*) w pliku *. XML* .|
|[Zadanie XSD](../msbuild/xsd-task.md)|Zawija narzędzie definicji schematu XML (*XSD. exe*), które generuje pliki schematu lub klasy ze źródła. *Zobacz uwagę poniżej.*|
|[Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)|Opisuje elementy systemu MSBuild.|
|[Zadania](../msbuild/msbuild-tasks.md)|Opisuje zadania, które są jednostkami kodu, które można połączyć w celu utworzenia kompilacji.|
|[Pisanie zadania](../msbuild/task-writing.md)|Opisuje sposób tworzenia zadania.|

> [!NOTE]
> Począwszy od programu Visual Studio 2017 C++ , obsługa projektu dla pliku *XSD. exe* jest przestarzała. Można nadal używać interfejsów API **Microsoft. VisualC. CppCodeProvider** , ręcznie dodając *CppCodeProvider. dll* do pamięci GAC.