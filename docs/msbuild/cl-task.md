---
title: CL — zadanie | Microsoft Docs
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
ms.openlocfilehash: effc1b51352052f4e11e42298f9e9567db30d8f1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593359"
---
# <a name="cl-task"></a>CL — Zadanie
Zawija narzędzie kompilatora firmy C++ Microsoft, *CL. exe*. Kompilator tworzy pliki wykonywalne ( *. exe*), pliki bibliotek dołączanych dynamicznie (*dll*) lub moduły kodu ( *. module*). Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options).

## <a name="parameters"></a>Parametry
 Na poniższej liście opisano parametry zadania **CL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

- **AdditionalIncludeDirectories**

   Opcjonalny parametr String [].

   Dodaje katalog do listy katalogów, które są przeszukiwane w poszukiwaniu plików dołączanych.

   Aby uzyskać więcej informacji, zobacz [/i (Dodatkowe katalogi dołączane)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Opcjonalny parametr ciągu.

   Lista opcji wiersza polecenia. Na przykład "/\<opcja1 >/\<opcja2 >/\<opcji # >". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania.

   Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Opcjonalny parametr String [].

   Określa katalog, który będzie przeszukiwany przez kompilator w celu rozpoznania odwołań do plików przesłanych do dyrektywy **#using** .

   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Opcjonalny parametr ciągu.

   Ciąg, który zawsze jest emitowany w wierszu polecenia. Wartość domyślna to " **/c**".

- **AssemblerListingLocation**

   Tworzy plik listy zawierający kod asemblera.

   Aby uzyskać więcej informacji, zobacz opcja **/Fa** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Opcjonalny parametr ciągu.

   Tworzy plik listy zawierający kod asemblera.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Nolisting** - *nie\<brak >*

  - **AssemblyCode** -  **/FA**

  - **AssemblyAndMachineCode** -  **/FAc**

  - **AssemblyAndSourceCode** -  **/FAs**

  - **Wszystkie** -  **/FACS**

    Aby uzyskać więcej informacji, zobacz Opcje **/Fa**, **/FAc**, **/FAS**i **/FACS** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Opcjonalny parametr ciągu.

   Włącza i wyłącza funkcję sprawdzania błędów czasu wykonywania w połączeniu z [runtime_checks](/cpp/preprocessor/runtime-checks) pragma.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Domyślne** -                           *\<brak >*

  - **StackFrameRuntimeCheck** -  **/RTCs**

  - **UninitializedLocalUsageCheck** -  **/RTCu**

  - **EnableFastChecks** -                           **/RTC1**

    Aby uzyskać więcej informacji, zobacz [/RTC (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Opcjonalny parametr logiczny.

   Jeśli `true`, program tworzy plik informacji o przeglądaniu.

   Aby uzyskać więcej informacji, zobacz opcja **/fr** w [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Opcjonalny parametr ciągu.

   Określa nazwę pliku dla pliku informacji o przeglądaniu.

   Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametr w tej tabeli, a także zobacz [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Opcjonalny parametr logiczny.

   Jeśli `true`, program wykryje pewne przepełnienia buforów, które zastępują adres zwrotny, typową technikę wykorzystywania kodu, który nie wymusza ograniczeń rozmiaru buforu.

   Aby uzyskać więcej informacji, zobacz [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Opcjonalny parametr logiczny.

   Jeśli `true`, wskazuje, że program **MSBuild** jest wywoływany przez IDE. W przeciwnym razie program **MSBuild** jest wywoływany w wierszu polecenia.

- **CallingConvention**

   Opcjonalny parametr ciągu.

   Określa konwencję wywoływania, która określa kolejność, w której argumenty funkcji są wypychane na stosie, niezależnie od tego, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję Name-dekorowania nazwy, która Kompilator używa do identyfikowania poszczególnych funkcji.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Cdecl** -  **/GD**

  - **FastCall** -                           **/Gr**

  - **StdCall** -                           **/Gz**

    Aby uzyskać więcej informacji, zobacz [/GD,/gr,/GV,/GZ (Konwencja wywoływania)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Opcjonalny parametr ciągu.

   Określa, czy plik wejściowy ma zostać skompilowany jako plik C++ C czy w pliku źródłowym.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Domyślne** -  *\<brak >*

  - **CompileAsC** -  **/TC**

  - **CompileAsCpp** -  **/TP**

    Aby uzyskać więcej informacji, zobacz [/TC,/TP,/TC,/TP (Określ typ pliku źródłowego)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Opcjonalny parametr ciągu.

   Umożliwia aplikacjom i składnikom korzystanie z funkcji środowiska uruchomieniowego języka wspólnego (CLR).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **wartość false** - *nie\<*

  - **true** -  **/clr**

  - **Czysty** -  **/CLR: Pure**

  - **Safe** -  **/clr:safe**

  - **OldSyntax** -  **/clr:oldSyntax**

    Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Opcjonalny parametr logiczny.

   Jeśli `true`, nakazuje kompilatorowi przygotowanie obrazu do zastosowania *poprawek na gorąco*. Ten parametr zapewnia, że pierwsza instrukcja każdej funkcji ma dwa bajty, co jest wymagane w przypadku stosowania poprawek na gorąco.

   Aby uzyskać więcej informacji, zobacz [/hotpatch (Create możliwy do poprawiania Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Opcjonalny parametr ciągu.

   Wybiera typ informacji o debugowaniu utworzonych dla programu oraz tego, czy te informacje są przechowywane w plikach obiektu ( *. obj*), czy w bazie danych programu (PDB).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **OldStyle** -  **/Z7**

  - **ProgramDatabase** -  **/Zi**

  - **EditAndContinue** -  **/ZI**

    Aby uzyskać więcej informacji, zobacz [/Z7,/Zi,/ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Opcjonalny parametr logiczny.

   Jeśli **wartość jest równa true**, instruuje kompilator, aby emituje błąd dla konstrukcji językowych, które nie są C++zgodne z ANSI C lub ANSI.

   Aby uzyskać więcej informacji, zobacz opcja **/za** w [/za,/ze (Wyłącz rozszerzenia językowe)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Opcjonalny parametr String [].

   Wyłącza numery ostrzeżeń, które są określone na liście rozdzielanej średnikami.

   Aby uzyskać więcej informacji, zobacz opcja `/wd` w [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Opcjonalny parametr ciągu.

   Określa architekturę generowania kodu, który używa instrukcji Streaming SIMD Extensions (SSE) i Streaming SIMD Extensions 2 (SSE2).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **StreamingSIMDExtensions** -  **/arch: SSE**

  - **StreamingSIMDExtensions2** -  **/arch: SSE2**

    Aby uzyskać więcej informacji, zobacz [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Opcjonalny parametr logiczny.

   Jeśli `true`, obsługuj bezpieczeństwo włókna danych przydzielone przy użyciu statycznego magazynu wątków lokalnych, czyli danych przydzielone przy użyciu `__declspec(thread)`.

   Aby uzyskać więcej informacji, zobacz [/gt (Obsługa bezpiecznego włókna — magazyn lokalny)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Opcjonalny parametr logiczny.

   Jeśli `true`, Włącz analizę kodu.

   Aby uzyskać więcej informacji, zobacz [/analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   Opcjonalny parametr ciągu.

   Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do firmy Microsoft. Domyślnie ustawienie w obszarze kompilacje IDE jest **monitem** , a ustawienie w kompilacjach w wierszu polecenia jest **kolejką**.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Brak** -  **/errorReport: brak**

  - **Monituj** -  **/errorReport: Prompt**

  - **Queue** -  **/errorReport:queue**

  - **Wyślij** -  **/errorReport: Send**

    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Opcjonalny parametr ciągu.

   Określa model obsługi wyjątków, który ma być używany przez kompilator.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **wartość false** - *nie\<*

  - **Async** -  **/EHa**

  - **Sync** -  **/EHsc**

  - **SyncCThrow** -  **/EHs**

    Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Opcjonalny parametr logiczny.

   Jeśli `true`, program tworzy plik listy z rozwiniętymi atrybutami, które zostały dodane do pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/FX (Scalanie wstrzykniętego kodu)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Opcjonalny parametr ciągu.

   Określa, czy ma być preferowany rozmiar kodu czy szybkość kodu.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Nie** -  *\<brak >*

  - **Rozmiar** -  **/OS**

  - **Szybkość** -  **/OT**

    Aby uzyskać więcej informacji, zobacz [/OS,/OT (Preferuj mały kod, Preferuj szybki kod)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Opcjonalny parametr logiczny.

   Jeśli `true`, włącza niezawodny model wyjątku zmiennoprzecinkowego. Wyjątki będą wywoływane natychmiast po ich wyzwoleniu.

   Aby uzyskać więcej informacji, zobacz opcję/**FP: except** w [/FP (Określ zachowanie zmiennoprzecinkowe)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Opcjonalny parametr ciągu.

   Ustawia model zmiennoprzecinkowy.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Precyzyjne** -  **/FP: precyzyjne**

  - **Strict** -  **/FP: Strict**

  - **Fast** -  **/fp:fast**

    Aby uzyskać więcej informacji, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Opcjonalny parametr logiczny.

   Jeśli `true`, implementuje standardowe C++ zachowanie programu [dla](/cpp/cpp/for-statement-cpp) pętli, które używają rozszerzeń Microsoft ([/ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Aby uzyskać więcej informacji, zobacz [/Zc: forScope (Wymuszaj zgodność w zakresie pętli for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Opcjonalny parametr `String[]`.

   Powoduje, że preprocesor przetwarza jeden lub więcej określonych plików nagłówkowych.

   Aby uzyskać więcej informacji, zobacz [/Fi (Nazwij plik z wymuszonym dołączeniem)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Opcjonalny parametr **String []** .

   Powoduje, że preprocesor przetwarza jeden lub więcej określonych **#using** plików.

   Aby uzyskać więcej informacji, zobacz [/Fu (nazwa pliku wymuszonego #using)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT).

   Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, powoduje, że kompilator przetwarza komentarze dokumentacji w plikach kodu źródłowego i tworzy plik *. xdc* dla każdego pliku kodu źródłowego, który zawiera komentarze dokumentacji.

   Aby uzyskać więcej informacji, zobacz [/doc (Przetwarzaj komentarze dokumentacji) (C++C/)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz również parametr **XMLDocumentationFileName** w tej tabeli.

- **IgnoreStandardIncludePath**

   Opcjonalny parametr `Boolean`.

   W przypadku `true`, uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w ścieżce i zawiera zmienne środowiskowe.

   Aby uzyskać więcej informacji, zobacz [/x (Ignoruj standardowe ścieżki dołączanych plików)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Opcjonalny parametr **ciągu** .

   Określa poziom rozwinięcia funkcji wbudowanej dla kompilacji.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Domyślne** -  *\<brak >*

  - **Wyłączone** -  **/Ob0**

  - **OnlyExplicitInline** -  **/Ob1**

  - **AnySuitable** -  **/Ob2**

    Aby uzyskać więcej informacji, zobacz [/ob (rozszerzenie funkcji wbudowanej)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, zastępuje pewne wywołania funkcji z wewnętrzną lub inną specjalną formą funkcji, która ułatwia działanie aplikacji.

   Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, umożliwia minimalną ponowną kompilację C++ , która określa, czy C++ pliki źródłowe, które zawierają zmienione definicje klas (przechowywane w plikach nagłówkowych (. h)), muszą być ponownie skompilowane.

   Aby uzyskać więcej informacji, zobacz [/GM (Włącz minimalną](/cpp/build/reference/gm-enable-minimal-rebuild)ponowną kompilację).

- **MultiProcessorCompilation**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, Użyj wielu procesorów do skompilowania. Ten parametr tworzy proces dla każdego efektywnego procesora na komputerze.

   Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](/cpp/build/reference/mp-build-with-multiple-processes). Zobacz również parametr **ProcessorNumber** w tej tabeli.

- **ObjectFileName**

   Opcjonalny parametr **ciągu** .

   Określa nazwę lub katalog pliku obiektu (. obj), który ma być używany zamiast domyślnego.

   Aby uzyskać więcej informacji, zobacz [/FO (nazwa pliku obiektu)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Opcjonalny parametr **String []** .

   Lista plików obiektów.

- **OmitDefaultLibName**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, pomija domyślną nazwę biblioteki wykonawczej C z pliku obiektu ( *. obj*). Domyślnie kompilator umieszcza nazwę biblioteki w pliku *. obj* , aby skierować konsolidator do odpowiedniej biblioteki.

   Aby uzyskać więcej informacji, zobacz [/zl (Pomiń domyślną nazwę biblioteki)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, pomija tworzenie wskaźników ramek na stosie wywołań.

   Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, powoduje, że kompilator przetwarza klauzule OpenMP i dyrektywy.

   Aby uzyskać więcej informacji, zobacz [/OpenMP (Włączanie obsługi openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optymalizacja**

   Opcjonalny parametr **ciągu** .

   Określa różne optymalizacje kodu dla szybkości i rozmiaru.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Wyłączone** -  **/od**

  - **MinSpace** -  **/O1**

  - **MaxSpeed** -  **/O2**

  - **Full** -  **/Ox**

    Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Opcjonalny parametr **ciągu** .

   Podczas kompilowania Utwórz lub użyj prekompilowanego pliku nagłówkowego ( *. PCH*).

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NotUsing** -  *\<brak >*

  - **Utwórz** -  **/YC**

  - **Użyj** -  **/Yu**

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

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, zachowuje komentarze podczas przetwarzania wstępnego.

   Aby uzyskać więcej informacji, zobacz [/c (Zachowaj komentarze podczas przetwarzania wstępnego)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Opcjonalny parametr `String[]`.

   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Opcjonalny parametr `ITaskItem[]`.

   Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.

- **PreprocessOutputPath**

   Opcjonalny parametr `String`.

   Określa nazwę pliku wyjściowego, do którego parametr **PreprocessToFile** zapisuje wstępnie przetworzone dane wyjściowe.

   Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Opcjonalny parametr `Boolean`.

   W przypadku `true`program wstępnie przetwarza pliki C C++ i Source oraz kopiuje wstępnie przetworzone pliki na standardowe urządzenie wyjściowe.

   Aby uzyskać więcej informacji, zobacz [/EP (wstępnie przetwórz do stdout bez dyrektyw #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Opcjonalny parametr `Boolean`.

   W przypadku `true`program wstępnie przetwarza pliki C C++ i Source oraz zapisuje wstępnie przetworzone dane wyjściowe do pliku.

   Aby uzyskać więcej informacji, zobacz [/p (Przetwarzaj wstępnie do pliku)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Opcjonalny parametr `Integer`.

   Określa maksymalną liczbę procesorów do użycia w kompilacji wieloprocesorowej. Tego parametru należy używać w połączeniu z parametrem **MultiProcessorCompilation** .

- **ProgramDataBaseFileName**

   Opcjonalny parametr `String`.

   Określa nazwę pliku bazy danych programu (PDB).

   Aby uzyskać więcej informacji, zobacz [/FD (nazwa pliku bazy danych programu)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Opcjonalny parametr `String`.

   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL, i wybiera wersje detaliczne lub debugowania biblioteki wykonawczej.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **MultiThreaded** -  **/MT**

  - **MultiThreadedDebug** -  **/MTd**

  - **MultiThreadedDLL** -  **/MD**

  - **MultiThreadedDebugDLL** -  **/MDd**

    Aby uzyskać więcej informacji, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, program dodaje kod do C++ sprawdzania typów obiektów w czasie wykonywania (informacje o typie czasu wykonywania).

   Aby uzyskać więcej informacji, zobacz [/gr (Włącz informacje typu run-time)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, powoduje, że kompilator wyprowadza listę plików dołączanych.

   Aby uzyskać więcej informacji, zobacz [/showIncludes (lista plików dołączanych)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, program zgłosi błąd czasu wykonywania, jeśli wartość zostanie przypisana do mniejszego typu danych i spowoduje utratę danych.

   Aby uzyskać więcej informacji, zobacz **/RTCc** Option in [/RTC (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **Źródeł**

   Wymagany `ITaskItem[]` parametr.

   Określa listę plików źródłowych rozdzielonych spacjami.

- **StringPooling**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, umożliwia kompilatorowi utworzenie jednej kopii identycznych ciągów w obrazie programu.

   Aby uzyskać więcej informacji, zobacz [/GF (eliminowanie ciągów zduplikowanych)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Opcjonalny parametr `String`.

   Określa wyrównanie bajtów dla wszystkich elementów członkowskich w strukturze.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Default** -  **/Zp1**

  - **1Byte** -  **/Zp1**

  - **2Bytes** -  **/Zp2**

  - **4Bytes** -  **/Zp4**

  - **8Bytes** -  **/Zp8**

  - **16Bytes** -  **/Zp16**

    Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie składowej struktury)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy)C++(C/)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **Katalog trackerlogdirectory**

   Opcjonalny parametr `String`.

   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.

- **TreatSpecificWarningsAsErrors**

   Opcjonalny parametr **String []** .

   Traktuje określoną listę ostrzeżeń kompilatora jako błędy.

   Aby uzyskać więcej informacji, zobacz opcja **/we**`n` w elemencie [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, Traktuj wszystkie ostrzeżenia kompilatora jako błędy.

   Aby uzyskać więcej informacji, zobacz **/WX** Option in [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, Traktuj typ `wchar_t` jako typ natywny.

   Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, oddefiniują symbole specyficzne dla firmy Microsoft, które definiuje kompilator.

   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Opcjonalny parametr `String[]`.

   Określa listę co najmniej jednego symbolu preprocesora do usunięcia.

   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, wyświetla pełną ścieżkę do plików kodu źródłowego przekazaną do kompilatora w diagnostyce.

   Aby uzyskać więcej informacji, zobacz [/FC (Pełna ścieżka pliku kodu źródłowego w diagnostyce)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, powoduje utworzenie pliku wyjściowego w formacie UTF-8.

   Aby uzyskać więcej informacji, zobacz opcja **/FAU** w [/FA,/FA (lista plików)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Opcjonalny parametr `String`.

   Określa najwyższy poziom ostrzeżeń, który ma zostać wygenerowany przez kompilator.

   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **TurnOffAllWarnings** -  **/W0**

  - **Level1** -  **/W1**

  - **Level2** -  **/W2**

  - **Level3** -  **/W3**

  - **Level4** -  **/W4**

  - **Włącz wszystkie ostrzeżenia** -  **/Wall**

    Aby uzyskać więcej informacji, zobacz sekcję **/w**_n_ w opcjach [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, włącza optymalizację całego programu.

   Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Opcjonalny parametr `String`.

   Określa nazwę wygenerowanego pliku dokumentacji XML. Ten parametr może być nazwą pliku lub katalogu.

   Aby uzyskać więcej informacji, zobacz argument `name` w [/doc (Przetwarzaj komentarze dokumentacji) (CC++/)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz również parametr **GenerateXMLDocumentationFiles** w tej tabeli.

- **MinimalRebuildFromTracking**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, wykonywana jest śledzona kompilacja przyrostowa; Jeśli `false`, wykonywana jest ponowna kompilacja.

- **TLogReadFiles**

   Opcjonalny parametr `ITaskItem[]`.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików odczytywane*.

   Dziennik śledzenia plików ( *. tlog*) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i są używane przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.

- **TLogWriteFiles**

   Opcjonalny parametr `ITaskItem[]`.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików zapisu*.

   Dziennik śledzenia plików zapisu ( *. tlog*) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie, i jest używany przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.

- **TrackFileAccess**

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, śledzi wzorce dostępu do plików.

   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
