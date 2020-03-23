---
title: Zadania MSBuild specyficzne dla języka C++ | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633151"
---
# <a name="msbuild-tasks-specific-to-c"></a>Zadania MSBuild specyficzne dla języka C++

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Po zainstalowaniu języka C++ dostępne są następujące zadania, oprócz tych, które są instalowane z msbuild. Aby uzyskać więcej informacji, zobacz [omówienie msbuild (C++).](/cpp/build/msbuild-visual-cpp-overview)

 Oprócz parametrów dla każdego zadania, każde zadanie ma również następujące parametry.

| Parametr | Opis |
|-------------------| - |
| `Condition` | Parametr `String` opcjonalny.<br /><br /> Wyrażenie `Boolean` używane przez aparat MSBuild do określenia, czy to zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków obsługiwanych przez MSBuild, zobacz [Warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndKontynuuj** lub **prawda**. Gdy zadanie nie powiedzie się, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i kompilacji są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie `Target` się, kolejne zadania w elemencie i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (domyślnie). Gdy zadanie zakończy się niepowodzeniem, pozostałe zadania w`Target` elemencie `Target` i kompilacji nie są wykonywane, a cały element i kompilacja są uważane za nieudane.<br /><br /> Wersje programu .NET Framework przed 4.5 `true` `false` obsługiwane tylko i wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Zadanie BscMake](../msbuild/bscmake-task.md)|Zawija narzędzie Narzędzia konserwacji informacji przeglądania przez firmę Microsoft *(bscmake.exe).*|
|[Zadanie CL](../msbuild/cl-task.md)|Zawija narzędzie kompilatora C++ (*cl.exe*).|
|[Zadanie CPPClean](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, które MSBuild tworzy podczas tworzenia projektu C++.|
|[Zadanie ClangCompile](../msbuild/clangcompile-task.md)|Zawija narzędzie kompilatora C++ (*clang.exe*).|
|[Zadanie CustomBuild](../msbuild/custombuild-task.md)|Zawija narzędzie kompilatora C++ (*cmd.exe*).|
|[Zadanie FXC](../msbuild/fxc-task.md)|Użyj kompilatorów modułów cieniowania HLSL w procesie kompilacji.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Odczytuje stare tlogs, zapisuje nowe tlogs i zwraca zestaw elementów, które nie są aktualne. (zadanie pomocnika)|
|[Nazwa pliku GetOutput](../msbuild/getoutputfilename-task.md)|Pobiera nazwę pliku wyjściowego dla cl i innych narzędzi, które umożliwiają określenie tylko katalogu wyjściowego lub pełnej nazwy pliku lub nic. (zadanie pomocnika)|
|[Zadanie LIB](../msbuild/lib-task.md)|Zawija narzędzie 32-bitowy Menedżer bibliotek microsoftowych (*lib.exe*).|
|[Zadanie łącza](../msbuild/link-task.md)|Zawija narzędzie konsolidatora języka C++ (*link.exe*).|
|[Zadanie MIDL](../msbuild/midl-task.md)|Zawija narzędzie kompilatora języka MIDL (MIDL) firmy Microsoft *(midl.exe).*|
|[Zadanie MT](../msbuild/mt-task.md)|Zawija narzędzie Microsoft Manifest Tool (*mt.exe*).|
|[Zadanie MultiToolTask](../msbuild/multitooltask-task.md)|Brak opisu.|
|[Zadanie ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Uruchom równoległe wystąpienia [zadania CustomBuild](../msbuild/custombuild-task.md).|
|[Zadanie rc](../msbuild/rc-task.md)|Zawija narzędzie Kompilator zasobów systemu Microsoft Windows *(rc.exe).*|
|[Zadanie SetEnv](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość określonej zmiennej środowiskowej.|
|[TrackedVCToolTask klasa podstawowa](../msbuild/trackedvctooltask-base-class.md)|Dziedziczy z [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Zadanie VCMessage](../msbuild/vcmessage-task.md)|Rejestruje komunikaty ostrzegawcze i komunikaty o błędach podczas kompilacji. (Nie można go wysunąć. Tylko do użytku wewnętrznego.)|
|[VCToolZadniak klasa podstawowa](../msbuild/vctooltask-base-class.md)|Dziedziczy z [narzędziaZadanie](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCZmiejęć zadanie](../msbuild/xdcmake-task.md)|Zawija narzędzie Dokumentacja XML *(xdcmake.exe),* które scala pliki dokumentu XML *(xdc)* w plik *xml.*|
|[Zadanie XSD](../msbuild/xsd-task.md)|Zawija narzędzie XML Schema Definition *(xsd.exe),* które generuje pliki schematu lub klasy ze źródła. *Patrz uwaga poniżej.*|
|[Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)|Opisuje elementy systemu MSBuild.|
|[Zadania](../msbuild/msbuild-tasks.md)|W tym artykule opisano zadania, które są jednostkami kodu, które można połączyć w celu utworzenia kompilacji.|
|[Pisanie zadań](../msbuild/task-writing.md)|W tym artykule opisano sposób tworzenia zadania.|

> [!NOTE]
> Począwszy od programu Visual Studio 2017, obsługa projektu C++ dla *xsd.exe* jest przestarzała. Nadal można używać interfejsów API **programu Microsoft.VisualC.CppCodeProvider,** ręcznie dodając *plik CppCodeProvider.dll* do pliku GAC.
