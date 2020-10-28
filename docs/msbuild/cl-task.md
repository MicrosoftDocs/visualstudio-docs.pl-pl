---
title: CL — zadanie | Microsoft Docs
description: Opisuje przeznaczenie i parametry zadania programu MSBuild CL, które Zawija narzędzie kompilatora języka Microsoft C++ cl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d930ed8d918a08503a6eaa6b60848abeec7683a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796839"
---
# <a name="cl-task"></a>CL — Zadanie

Zawija narzędzie kompilatora języka Microsoft C++ *cl.exe* . Kompilator tworzy pliki wykonywalne ( *. exe* ), pliki bibliotek dołączanych dynamicznie ( *dll* ) lub moduły kodu ( *. module* ). Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options) i [Użyj programu MSBuild z wiersza polecenia](/cpp/build/msbuild-visual-cpp) i [Użyj zestawu narzędzi Microsoft C++ w wierszu polecenia](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Na poniższej liście opisano parametry zadania **CL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

- **AdditionalIncludeDirectories**

   Opcjonalny parametr String [].

   Dodaje katalog do listy katalogów, które są przeszukiwane w poszukiwaniu plików dołączanych.

   Aby uzyskać więcej informacji, zobacz [/i (Dodatkowe katalogi dołączane)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Opcjonalny parametr ciągu.

   Lista opcji wiersza polecenia. Na przykład "/ \<option1>  / \<option2>  / \<option#> ". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania.

   Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Opcjonalny parametr String [].

   Określa katalog, który będzie przeszukiwany przez kompilator w celu rozpoznania odwołań do plików przesłanych do dyrektywy **#using** .

   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Opcjonalny parametr ciągu.

   Ciąg, który zawsze jest emitowany w wierszu polecenia. Wartość domyślna to " **/c** ".

- **AssemblerListingLocation**

   Tworzy plik listy zawierający kod asemblera.

   Aby uzyskać więcej informacji, zobacz opcja **/Fa** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Opcjonalny parametr ciągu.

   Tworzy plik listy zawierający kod asemblera.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Nolisting** - *\<none>*

  - **AssemblyCode**  -  **/FA**

  - **AssemblyAndMachineCode**  -  **/FAc**

  - **AssemblyAndSourceCode**  -  **/FAS**

  - **Wszystkie**  -  **/FACS**

    Aby uzyskać więcej informacji, zobacz Opcje **/Fa** , **/FAc** , **/FAS** i **/FACS** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Opcjonalny parametr ciągu.

   Włącza i wyłącza funkcję sprawdzania błędów czasu wykonywania w połączeniu z [runtime_checks](/cpp/preprocessor/runtime-checks) pragma.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wartooć** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Aby uzyskać więcej informacji, zobacz [/RTC (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Opcjonalny parametr logiczny.

   Jeśli `true` , program tworzy plik informacji o przeglądaniu.

   Aby uzyskać więcej informacji, zobacz opcja **/fr** w [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Opcjonalny parametr ciągu.

   Określa nazwę pliku dla pliku informacji o przeglądaniu.

   Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametr w tej tabeli, a także zobacz [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Opcjonalny parametr logiczny.

   Jeśli `true` program wykryje pewne przepełnienia buforów, które zastępują adres zwrotny, typową techniką wykorzystania kodu, który nie wymusza ograniczeń rozmiaru buforu.

   Aby uzyskać więcej informacji, zobacz [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Opcjonalny parametr logiczny.

   Jeśli `true` , wskazuje, że program **MSBuild** jest wywoływany przez IDE. W przeciwnym razie program **MSBuild** jest wywoływany w wierszu polecenia.

- **CallingConvention**

   Opcjonalny parametr ciągu.

   Określa konwencję wywoływania, która określa kolejność, w której argumenty funkcji są wypychane na stosie, niezależnie od tego, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję Name-dekorowania nazwy, której kompilator używa do identyfikacji poszczególnych funkcji.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **CDECL**  -  **/GD**

  - **FastCall**  -                           **/Gr**

  - **Stdcall**  -                           **/GZ**

    Aby uzyskać więcej informacji, zobacz [/GD,/gr,/GV,/GZ (Konwencja wywoływania)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Opcjonalny parametr ciągu.

   Określa, czy kompilować plik wejściowy jako plik źródłowy C lub C++.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wartooć** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Aby uzyskać więcej informacji, zobacz [/TC,/TP,/TC,/TP (Określ typ pliku źródłowego)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Opcjonalny parametr ciągu.

   Umożliwia aplikacjom i składnikom korzystanie z funkcji środowiska uruchomieniowego języka wspólnego (CLR).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **false** - *\<none>*

  - **wartość true**  -  **/CLR**

  - **Czysty**  -  **/CLR: Pure**

  - **Bezpieczne**  -  **/CLR: Safe**

  - **OldSyntax**  -  **/CLR: oldSyntax**

    Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Opcjonalny parametr logiczny.

   Jeśli `true` , nakazuje kompilatorowi przygotowanie obrazu do zastosowania *poprawek na gorąco* . Ten parametr zapewnia, że pierwsza instrukcja każdej funkcji ma dwa bajty, co jest wymagane w przypadku stosowania poprawek na gorąco.

   Aby uzyskać więcej informacji, zobacz [/hotpatch (Create możliwy do poprawiania Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Opcjonalny parametr ciągu.

   Wybiera typ informacji o debugowaniu utworzonych dla programu oraz tego, czy te informacje są przechowywane w plikach obiektu ( *. obj* ), czy w bazie danych programu (PDB).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **OldStyle**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/Zi**

    Aby uzyskać więcej informacji, zobacz [/Z7,/Zi,/ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Opcjonalny parametr logiczny.

   Jeśli **ma wartość true** , instruuje kompilator, aby emituje błąd dla konstrukcji językowych, które nie są zgodne ze standardem ANSI C lub ANSI C++.

   Aby uzyskać więcej informacji, zobacz opcja **/za** w [/za,/ze (Wyłącz rozszerzenia językowe)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Opcjonalny parametr String [].

   Wyłącza numery ostrzeżeń, które są określone na liście rozdzielanej średnikami.

   Aby uzyskać więcej informacji, zobacz `/wd` Opcje w opcjach [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Opcjonalny parametr ciągu.

   Określa architekturę generowania kodu, który używa instrukcji Streaming SIMD Extensions (SSE) i Streaming SIMD Extensions 2 (SSE2).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **StreamingSIMDExtensions**  -  **/arch: SSE**

  - **StreamingSIMDExtensions2**  -  **/arch: SSE2**

    Aby uzyskać więcej informacji, zobacz [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Opcjonalny parametr logiczny.

   Jeśli `true` firma obsługuje zabezpieczenia włókna danych przydzielone przy użyciu statycznego magazynu wątków lokalnych, to znaczy dane przydzielone za pomocą `__declspec(thread)` .

   Aby uzyskać więcej informacji, zobacz [/gt (Obsługa bezpiecznego włókna — magazyn lokalny)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Opcjonalny parametr logiczny.

   Jeśli `true` , Włącz analizę kodu.

   Aby uzyskać więcej informacji, zobacz [/analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   Opcjonalny parametr ciągu.

   Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do firmy Microsoft. Domyślnie ustawienie w obszarze kompilacje IDE jest **monitem** , a ustawienie w kompilacjach w wierszu polecenia jest **kolejką** .

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Brak**  -  **/errorReport: brak**

  - **Monituj**  -  **/errorReport: Monituj**

  - **Kolejka**  -  **/errorReport: Queue**

  - **Wyślij**  -  **/errorReport: Wyślij**

    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Opcjonalny parametr ciągu.

   Określa model obsługi wyjątków, który ma być używany przez kompilator.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **false** - *\<none>*

  - **Async**  -  **/EHa**

  - **Synchronizacja**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHS**

    Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Opcjonalny parametr logiczny.

   Jeśli `true` program utworzy plik listy z rozwiniętymi atrybutami, które zostały dodane do pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/FX (Scalanie wstrzykniętego kodu)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Opcjonalny parametr ciągu.

   Określa, czy ma być preferowany rozmiar kodu czy szybkość kodu.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Zarówno** - *\<none>*

  - **Rozmiar**  -  **/OS**

  - **Szybkość**  -  **/OT**

    Aby uzyskać więcej informacji, zobacz [/OS,/OT (Preferuj mały kod, Preferuj szybki kod)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Opcjonalny parametr logiczny.

   Jeśli `true` , włącza niezawodny model wyjątku zmiennoprzecinkowego. Wyjątki będą wywoływane natychmiast po ich wyzwoleniu.

   Aby uzyskać więcej informacji, zobacz opcję/ **FP: except** w [/FP (Określ zachowanie zmiennoprzecinkowe)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Opcjonalny parametr ciągu.

   Ustawia model zmiennoprzecinkowy.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Precyzyjna**  -  **/FP: Precyzyjna**

  - **Strict**  -  **/FP: Strict**

  - **Szybkie**  -  **/FP: szybka**

    Aby uzyskać więcej informacji, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Opcjonalny parametr logiczny.

   Jeśli `true` , implementuje standardowe zachowanie języka C++ w programie [dla](/cpp/cpp/for-statement-cpp) pętli, które używają rozszerzeń Microsoft ([/ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Aby uzyskać więcej informacji, zobacz [/Zc: forScope (Wymuszaj zgodność w zakresie pętli for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Opcjonalny `String[]` parametr.

   Powoduje, że preprocesor przetwarza jeden lub więcej określonych plików nagłówkowych.

   Aby uzyskać więcej informacji, zobacz [/Fi (Nazwij plik z wymuszonym dołączeniem)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Opcjonalny parametr **String []** .

   Powoduje, że preprocesor przetwarza jeden lub więcej określonych **#using** plików.

   Aby uzyskać więcej informacji, zobacz [/Fu (nazwa pliku wymuszonego #using)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT).

   Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , powoduje, że kompilator przetwarza komentarze dokumentacji w plikach kodu źródłowego i tworzy plik *. xdc* dla każdego pliku kodu źródłowego, który zawiera komentarze dokumentacji.

   Aby uzyskać więcej informacji, zobacz [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz również parametr **XMLDocumentationFileName** w tej tabeli.

- **IgnoreStandardIncludePath**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , program uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w ścieżce i zawiera zmienne środowiskowe.

   Aby uzyskać więcej informacji, zobacz [/x (Ignoruj standardowe ścieżki dołączanych plików)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Opcjonalny parametr **ciągu** .

   Określa poziom rozwinięcia funkcji wbudowanej dla kompilacji.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wartooć** - *\<none>*

  - **Wyłączony**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/OB1**

  - **AnySuitable**  -  **/Ob2**

    Aby uzyskać więcej informacji, zobacz [/ob (rozszerzenie funkcji wbudowanej)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Opcjonalny `Boolean` parametr.

   W przypadku `true` zastąpienia niektórych wywołań funkcji za pomocą wewnętrznych lub w inny sposób specjalnych form funkcji, która ułatwia działanie aplikacji.

   Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` program włączy minimalną ponowną kompilację, która określa, czy pliki źródłowe c++, które zawierają zmienione definicje klas c++ (przechowywane w plikach nagłówkowych (h)), muszą być ponownie skompilowane.

   Aby uzyskać więcej informacji, zobacz [/GM (Włącz minimalną](/cpp/build/reference/gm-enable-minimal-rebuild)ponowną kompilację).

- **MultiProcessorCompilation**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` używasz wielu procesorów do kompilowania. Ten parametr tworzy proces dla każdego efektywnego procesora na komputerze.

   Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](/cpp/build/reference/mp-build-with-multiple-processes). Zobacz również parametr **ProcessorNumber** w tej tabeli.

- **ObjectFileName**

   Opcjonalny parametr **ciągu** .

   Określa nazwę lub katalog pliku obiektu (. obj), który ma być używany zamiast domyślnego.

   Aby uzyskać więcej informacji, zobacz [/FO (nazwa pliku obiektu)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Opcjonalny parametr **String []** .

   Lista plików obiektów.

- **OmitDefaultLibName**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , pomija domyślną nazwę biblioteki wykonawczej C z pliku obiektu ( *. obj* ). Domyślnie kompilator umieszcza nazwę biblioteki w pliku *. obj* , aby skierować konsolidator do odpowiedniej biblioteki.

   Aby uzyskać więcej informacji, zobacz [/zl (Pomiń domyślną nazwę biblioteki)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , pomija tworzenie wskaźników ramek na stosie wywołań.

   Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , powoduje, że kompilator przetwarza klauzule OpenMP i dyrektywy.

   Aby uzyskać więcej informacji, zobacz [/OpenMP (Włączanie obsługi openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optymalizacja**

   Opcjonalny parametr **ciągu** .

   Określa różne optymalizacje kodu dla szybkości i rozmiaru.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wyłączony**  -  **/Od**

  - **MinSpace**  -  **/O1**

  - **MaxSpeed**  -  **/O2**

  - **Pełny**  -  **/OX**

    Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Opcjonalny parametr **ciągu** .

   Podczas kompilowania Utwórz lub użyj prekompilowanego pliku nagłówkowego ( *. PCH* ).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NotUsing** - *\<none>*

  - **Utwórz**  -  **/YC**

  - **Użyj**  -  **/Yu**

    Aby uzyskać więcej informacji, zobacz [/YC (Create prekompilowany plik nagłówkowy)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Użyj prekompilowanego pliku nagłówkowego)](/cpp/build/reference/yu-use-precompiled-header-file). Zobacz również parametry **PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** w tej tabeli.

- **PrecompiledHeaderFile**

   Opcjonalny parametr **ciągu** .

   Określa nazwę prekompilowanego pliku nagłówkowego do utworzenia lub użycia.

   Aby uzyskać więcej informacji, zobacz [/YC (Create prekompilowany plik nagłówkowy)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Użyj prekompilowanego pliku nagłówkowego)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Opcjonalny parametr **ciągu** .

   Określa nazwę ścieżki prekompilowanego nagłówka zamiast używania domyślnej nazwy ścieżki.

   Aby uzyskać więcej informacji, zobacz [/FP (nazwa pliku. pch)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Opcjonalny `Boolean` parametr.

   If `true` zachowuje komentarze podczas przetwarzania wstępnego.

   Aby uzyskać więcej informacji, zobacz [/c (Zachowaj komentarze podczas przetwarzania wstępnego)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Opcjonalny `String[]` parametr.

   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Opcjonalny `ITaskItem[]` parametr.

   Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.

- **PreprocessOutputPath**

   Opcjonalny `String` parametr.

   Określa nazwę pliku wyjściowego, do którego parametr **PreprocessToFile** zapisuje wstępnie przetworzone dane wyjściowe.

   Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` program wstępnie przetworzy pliki źródłowe C i C++ i skopiuje wstępnie przetworzone pliki na standardowe urządzenie wyjściowe.

   Aby uzyskać więcej informacji, zobacz [/EP (wstępnie przetwórz do stdout bez dyrektyw #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` program wstępnie przetworzy pliki źródłowe C i C++ i zapisze wstępnie przetworzone dane wyjściowe do pliku.

   Aby uzyskać więcej informacji, zobacz [/p (Przetwarzaj wstępnie do pliku)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Opcjonalny `Integer` parametr.

   Określa maksymalną liczbę procesorów do użycia w kompilacji wieloprocesorowej. Tego parametru należy używać w połączeniu z parametrem **MultiProcessorCompilation** .

- **ProgramDataBaseFileName**

   Opcjonalny `String` parametr.

   Określa nazwę pliku bazy danych programu (PDB).

   Aby uzyskać więcej informacji, zobacz [/FD (nazwa pliku bazy danych programu)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Opcjonalny `String` parametr.

   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL, i wybiera wersje detaliczne lub debugowania biblioteki wykonawczej.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wielowątkowe**  -  **/MT**

  - **MultiThreadedDebug**  -  **/MTD**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDD**

    Aby uzyskać więcej informacji, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie czasu wykonywania).

   Aby uzyskać więcej informacji, zobacz [/gr (Włącz informacje typu run-time)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , powoduje, że kompilator wyprowadza listę plików dołączanych.

   Aby uzyskać więcej informacji, zobacz [/showIncludes (lista plików dołączanych)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` program zgłosi błąd czasu wykonywania, jeśli wartość zostanie przypisana do mniejszego typu danych i spowoduje utratę danych.

   Aby uzyskać więcej informacji, zobacz **/RTCc** Option in [/RTC (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **Źródeł**

   Wymagany parametr interfejsu `ITaskItem[]`.

   Określa listę plików źródłowych rozdzielonych spacjami.

- **StringPooling**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , umożliwia kompilatorowi utworzenie jednej kopii identycznych ciągów w obrazie programu.

   Aby uzyskać więcej informacji, zobacz [/GF (eliminowanie ciągów zduplikowanych)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Opcjonalny `String` parametr.

   Określa wyrównanie bajtów dla wszystkich elementów członkowskich w strukturze.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wartość domyślna**  -  **/ZP1**

  - **1Byte**  -  **/ZP1**

  - **2Bytes**  -  **/Zp2**

  - **4Bytes**  -  **/Zp4**

  - **8Bytes**  -  **/ZP8**

  - **16Bytes**  -  **/Zp16**

    Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie składowej struktury)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **Katalog trackerlogdirectory**

   Opcjonalny `String` parametr.

   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.

- **TreatSpecificWarningsAsErrors**

   Opcjonalny parametr **String []** .

   Traktuje określoną listę ostrzeżeń kompilatora jako błędy.

   Aby uzyskać więcej informacji, zobacz **/we** `n` opcja w [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` wszystkie ostrzeżenia kompilatora mają być traktowane jako błędy.

   Aby uzyskać więcej informacji, zobacz **/WX** Option in [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` Typ ma być traktowany `wchar_t` jako typ natywny.

   Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , definiuje zdefiniowane przez kompilator symbole specyficzne dla firmy Microsoft.

   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Opcjonalny `String[]` parametr.

   Określa listę co najmniej jednego symbolu preprocesora do usunięcia.

   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , wyświetla pełną ścieżkę do plików kodu źródłowego przekazaną do kompilatora w diagnostyce.

   Aby uzyskać więcej informacji, zobacz [/FC (Pełna ścieżka pliku kodu źródłowego w diagnostyce)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , powoduje, że plik wyjściowy zostanie utworzony w formacie UTF-8.

   Aby uzyskać więcej informacji, zobacz opcja **/FAU** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Opcjonalny `String` parametr.

   Określa najwyższy poziom ostrzeżeń, który ma zostać wygenerowany przez kompilator.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Level1**  -  **/W1**

  - **Level2**  -  **/W2**

  - **LEVEL3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **Włącz wszystkie ostrzeżenia**  -  **/Wall**

    Aby uzyskać więcej informacji, zobacz sekcję **/w**_n_ w opcjach [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` , włącza optymalizację całego programu.

   Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Opcjonalny `String` parametr.

   Określa nazwę wygenerowanego pliku dokumentacji XML. Ten parametr może być nazwą pliku lub katalogu.

   Aby uzyskać więcej informacji, zobacz `name` argument w [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz również parametr **GenerateXMLDocumentationFiles** w tej tabeli.

- **MinimalRebuildFromTracking**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` jest wykonywana śledzona kompilacja przyrostowa; w przypadku `false` przetworzenia odbudowy.

- **TLogReadFiles**

   Opcjonalny `ITaskItem[]` parametr.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików odczytywane* .

   Dziennik śledzenia plików ( *. tlog* ) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i są używane przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.

- **TLogWriteFiles**

   Opcjonalny `ITaskItem[]` parametr.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików zapisu* .

   Dziennik śledzenia plików zapisu ( *. tlog* ) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie, i jest używany przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.

- **TrackFileAccess**

   Opcjonalny `Boolean` parametr.

   Jeśli `true` śledzi wzorce dostępu do plików.

   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
