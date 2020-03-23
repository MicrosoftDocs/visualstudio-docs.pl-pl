---
title: Cl Zadanie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865339"
---
# <a name="cl-task"></a>CL — Zadanie

Zawija narzędzie kompilatora Microsoft C++, *cl.exe*. Kompilator tworzy pliki wykonywalne (*.exe*), pliki biblioteki dynamicznego łącza (*.dll*) lub moduł kodu (*.netmodule*). pliki. Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options) i [Użyj MSBuild z wiersza polecenia](/cpp/build/msbuild-visual-cpp) i Użyj zestawu narzędzi Microsoft [C++ z wiersza polecenia](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Na poniższej liście opisano parametry zadania **CL.** Większość parametrów zadania i kilka zestawów parametrów odpowiada opcji wiersza polecenia.

- **DodatkoweInobserwająKatary**

   Parametr Opcjonalny ciąg[].

   Dodaje katalog do listy katalogów, które są wyszukiwane pliki dołączania.

   Aby uzyskać więcej informacji, zobacz [/I (Dodatkowe katalogi dołączane)](/cpp/build/reference/i-additional-include-directories).

- **Dodatkoweopcje**

   Opcjonalny parametr String.

   Lista opcji wiersza polecenia. Na przykład "/\<option1>\</ option2>\</ option#>". Ten parametr służy do określania opcji wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania.

   Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](/cpp/build/reference/compiler-options).

- **DodatkoweUżywanieKatalogi**

   Parametr Opcjonalny ciąg[].

   Określa katalog, który kompilator będzie przeszukiwać w celu rozpoznawania odwołań do plików przekazanych do **dyrektywy #using.**

   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych).](/cpp/build/reference/ai-specify-metadata-directories)

- **ZawszePotwierdzaj**

   Opcjonalny parametr String.

   Ciąg, który zawsze jest emitowany w wierszu polecenia. Jego wartością domyślną jest "**/c**".

- **AsembleraListingLokalizacja**

   Tworzy plik aukcji, który zawiera kod zestawu.

   Aby uzyskać więcej informacji, zobacz **/Fa** opcja w [/FA, /Fa (plik aukcji)](/cpp/build/reference/fa-fa-listing-file).

- **AkceserOutput**

   Opcjonalny parametr String.

   Tworzy plik aukcji, który zawiera kod zestawu.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NoListing** - *\<brak>*

  - **Kod zestawu****/FA**  - 

  - **AssemblyAndMachineCode** - **/FAc**

  - **AssemblyAndSourceCode** - **/FAs**

  - **Wszystkie** - **/FAcs**

    Aby uzyskać więcej informacji, zobacz **/FA**, **/FAc**, **/FAs**i **/FAcs** options in [/FA, /Fa (Listing file)](/cpp/build/reference/fa-fa-listing-file).

- **Podstawowe czeki ścięci**

   Opcjonalny parametr String.

   Włącza i wyłącza funkcję sprawdzania błędów w czasie wykonywania w połączeniu z pragmą [runtime_checks.](/cpp/preprocessor/runtime-checks)

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Domyślnie brak** -                          >*\<*

  - **StackFrameRuntimeCheck** - **/RTC**

  - **NiezainicjowanaLokalNalokalna kontrola** - **/RTCu**

  - **EnableFastChecks** -                          **/RTC1**

    Aby uzyskać więcej informacji, zobacz [/RTC (Sprawdzanie błędów w czasie wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **Przeglądajinformatację**

   Opcjonalny parametr logiczny.

   Jeśli `true`, tworzy plik informacji przeglądania.

   Aby uzyskać więcej informacji, zobacz **/FR** opcja w [/FR, /Fr (Create .sbr file)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **Przeglądajinformacyjny plik**

   Opcjonalny parametr String.

   Określa nazwę pliku informacji przeglądania.

   Aby uzyskać więcej informacji, zobacz parametr **BrowseInformation** w tej tabeli, a także zobacz [/FR, /Fr (Create .sbr file)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **Sprawdzanie zabezpieczeń bufora**

   Opcjonalny parametr logiczny.

   Jeśli `true`, wykrywa niektóre przepełnienia buforu, które zastępują adres zwrotny, powszechną techniką wykorzystania kodu, który nie wymusza ograniczeń rozmiaru buforu.

   Aby uzyskać więcej informacji, zobacz [/GS (Kontrola zabezpieczeń buforu)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE (BudynekInIDE)**

   Opcjonalny parametr logiczny.

   Jeśli `true`, wskazuje, że **MSBuild** jest wywoływany przez IDE. W przeciwnym razie **MSBuild** jest wywoływany w wierszu polecenia.

- **Callingconvention**

   Opcjonalny parametr String.

   Określa konwencję wywołującą, która określa kolejność, w jakiej argumenty funkcji są wypychane na stosie, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz konwencję dekorowania nazw, która kompilator używa do identyfikowania poszczególnych funkcji.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Cdecl** - **/Gd**

  - **FastCall** -                          **/Gr**

  - **StdCall** -                          **/Gz**

    Aby uzyskać więcej informacji, zobacz [/Gd, /Gr, /Gv, /Gz (konwencja wywoływania)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **KompilacjeA**

   Opcjonalny parametr String.

   Określa, czy plik wejściowy ma być kompilowany jako plik źródłowy języka C lub C++.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Domyślnie brak** - >*\<*

  - **CompileAsC** - **/TC**

  - **CompileAsCpp** - **/TP**

    Aby uzyskać więcej informacji, zobacz [/Tc, /Tp, /TC, /TP (Określ source file type)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Opcjonalny parametr String.

   Umożliwia aplikacjom i składnikom korzystanie z funkcji ze środowiska wykonawczego języka wspólnego (CLR).

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **false** - *none>\<*

  - **prawda** - **/clr**

  - **Czysty** - **/clr:czysty**

  - **Bezpieczny** - **/clr:bezpieczny**

  - **StarySyntax** - **/clr:oldSyntax**

    Aby uzyskać więcej informacji, zobacz [/clr (Kompilacja środowiska wykonawczego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Opcjonalny parametr logiczny.

   Jeśli `true`, informuje kompilator, aby przygotować obraz do *hot patching*. Ten parametr zapewnia, że pierwsza instrukcja każdej funkcji jest dwa bajty, co jest wymagane do hot patching.

   Aby uzyskać więcej informacji, zobacz [/hotpatch (Tworzenie obrazu hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Opcjonalny parametr String.

   Wybiera typ informacji debugowania utworzonych dla programu i czy te informacje są przechowywane w plikach obiektu (*.obj*) lub w bazie danych programu (PDB).

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **OldStyle** - **/Z7**

  - **ProgramDatabase** - **/Zi**

  - **EditAndKontynuuj** - **/ZI**

    Aby uzyskać więcej informacji, zobacz [/Z7, /Zi, /ZI (format informacji debugowania).](/cpp/build/reference/z7-zi-zi-debug-information-format)

- **DisableLanguageExtensions (Nie wyłączanie języka)**

   Opcjonalny parametr logiczny.

   Jeśli **true**, informuje kompilator emitować błąd dla konstrukcji języka, które nie są zgodne z ANSI C lub ANSI C ++.

   Aby uzyskać więcej informacji, zobacz **/Za** opcja w [/Za, /Ze (Wyłącz rozszerzenia języka)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings (Nie wyłączajwarczości)**

   Parametr Opcjonalny ciąg[].

   Wyłącza numery ostrzeżeń, które są określone na liście rozdzielane średnikami.

   Aby uzyskać więcej `/wd` informacji, zobacz opcję w [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /wo, /wo, /Wv, /WX (poziom ostrzeżenia).](/cpp/build/reference/compiler-option-warning-level)

- **Zestaw EnableEnhancedInstruction**

   Opcjonalny parametr String.

   Określa architekturę generowania kodu, która używa instrukcji rozszerzenia SIMD (SSE) i przesyłania strumieniowego rozszerzeń SIMD 2 (SSE2).

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **StreamingSIMDExtensions** - **/arch:SSE**

  - **StreamingSIMDExtensions2** - **/arch:SSE2**

    Aby uzyskać więcej informacji, zobacz [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations (Ekwolonalizowania)**

   Opcjonalny parametr logiczny.

   Jeśli `true`, obsługa bezpieczeństwa światłowodu dla danych przydzielonych przy użyciu statycznego wątku lokalnego magazynu, czyli dane przydzielone za pomocą . `__declspec(thread)`

   Aby uzyskać więcej informacji, zobacz [/GT (Obsługa pamięci masowej lokalnej z włóknem bezpieczeństwa światłowodowego).](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage)

- **EnablePREfast (Umożliwianie preszystyk**

   Opcjonalny parametr logiczny.

   Jeśli `true`włącz analizę kodu.

   Aby uzyskać więcej informacji, zobacz [/analizowanie (analiza kodu)](/cpp/build/reference/analyze-code-analysis).

- **Raportowanie błędów**

   Opcjonalny parametr String.

   Umożliwia podanie informacji o błędzie kompilatora wewnętrznego (ICE) bezpośrednio do firmy Microsoft. Domyślnie ustawieniem w kompilacjach IDE jest **Monit,** a ustawieniem w kompilacjach wiersza polecenia jest **Kolejka**.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Brak** - **/errorReport:none**

  - **Monituj** - **/errorReport:prompt**

  - **Kolejka** - **/errorReport:queue**

  - **Wyślij** - **/errorReport:send**

    Aby uzyskać więcej informacji, zobacz [/errorReport (Raport błędów kompilatora wewnętrznego)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **Obsługa wyjątków**

   Opcjonalny parametr String.

   Określa model obsługi wyjątków, który ma być używany przez kompilator.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **false** - *none>\<*

  - **Async** - **/EHa**

  - **Synchronizacja** - **/EHsc**

  - **SyncCThrow** - **/EHs**

    Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątków)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource (Zniewaź ze)**

   Opcjonalny parametr logiczny.

   Jeśli `true`program , tworzy plik aukcji, który ma rozwinięte atrybuty wstrzyknięte do pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/Fx (Merge injected code)](/cpp/build/reference/fx-merge-injected-code).

- **Prędkość faworyzowania**

   Opcjonalny parametr String.

   Określa, czy rozmiar kodu lub szybkość kodu mają być preferowane.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Ani żadna** - *\<>*

  - **Rozmiar** - **/Os**

  - **Prędkość** - **/Ot**

    Aby uzyskać więcej informacji, zobacz [/Os, /Ot (Favor small code, favor fast code)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions (Nieokreślenia floating**

   Opcjonalny parametr logiczny.

   Jeśli `true`, włącza niezawodny model wyjątku zmiennoprzecinkowego. Wyjątki zostaną podniesione natychmiast po ich wyzwoleniu.

   Aby uzyskać więcej informacji, zobacz /**fp:except** opcja w [/fp (Określanie zachowania zmiennoprzecinkowego)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel (Pływający Program Programu**

   Opcjonalny parametr String.

   Ustawia model zmiennoprzecinowy.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Precyzja** - **/fp:precyzyjna**

  - **Ścisłe** - **/fp:ścisłe**

  - **Szybko** - **/fp:szybko**

    Aby uzyskać więcej informacji, zobacz [/fp (Określanie zachowania zmiennoprzecinkowego)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope (ForceConformanceInForLoopScope)**

   Opcjonalny parametr logiczny.

   Jeśli `true`, implementuje standardowe zachowanie języka C++ w [przypadku](/cpp/cpp/for-statement-cpp) pętli korzystających z rozszerzeń firmy Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Aby uzyskać więcej informacji, zobacz [/Zc:forScope (Wymuś zgodność w zakresie pętli)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **Wymuszonewłącza pliki**

   Parametr `String[]` opcjonalny.

   Powoduje, że preprocesor przetwarza jeden lub więcej określonych plików nagłówkowych.

   Aby uzyskać więcej informacji, zobacz [/FI (Nazwa wymuszona plik dołączania)](/cpp/build/reference/fi-name-forced-include-file).

- **Wymuszone pouczanie plików**

   Parametr **Opcjonalny ciąg[].**

   Powoduje, że preprocesor przetwarzać jeden lub więcej określonych **#using** plików.

   Aby uzyskać więcej informacji, zobacz [/FU (Nazwa wymuszona #using pliku)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking (FunkcjaPoziomowanie łączące)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, umożliwia kompilator do pakowania poszczególnych funkcji w postaci funkcji pakietowych (COMDATs).

   Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](/cpp/build/reference/gy-enable-function-level-linking).

- **Generowanie plików dodokumentacji XML**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program Kompilator powoduje, że kompilator przetwarza komentarze dokumentacji w plikach kodu źródłowego i tworzy plik *xdc* dla każdego pliku kodu źródłowego zawierającego komentarze do dokumentacji.

   Aby uzyskać więcej informacji, zobacz [/doc (Komentarze do dokumentacji procesu) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz także **parametr XMLDocumentationFileName** w tej tabeli.

- **IgnoreStandardIncludePath**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program ,uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w zmiennych środowiskowych PATH i INCLUDE.

   Aby uzyskać więcej informacji, zobacz [/X (Ignoruj standardowe ścieżki dołączania)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionRozwińRozwiń**

   Opcjonalny parametr **String.**

   Określa poziom rozszerzenia funkcji wbudowanych dla kompilacji.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Domyślnie brak** - >*\<*

  - **Wyłączone** - **/Ob0**

  - **TylkoExplicitInline** - **/Ob1**

  - **AnySuitable** - **/Ob2**

    Aby uzyskać więcej informacji, zobacz [/Ob (Rozszerzenie funkcji wbudowanej)](/cpp/build/reference/ob-inline-function-expansion).

- **Wewnętrzne funkcje**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, zastępuje niektóre wywołania funkcji z wewnętrznych lub w inny sposób specjalnych form funkcji, które pomagają aplikacji działać szybciej.

   Aby uzyskać więcej informacji, zobacz [/Oi (Generowanie funkcji wewnętrznych)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, umożliwia minimalne przebudowy, która określa, czy pliki źródłowe języka C++, które zawierają zmienione definicje klas C++ (przechowywane w plikach nagłówka (.h) muszą być ponownie skompilowane.

   Aby uzyskać więcej informacji, zobacz [/Gm (Włącz minimalne przebudowy)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **Kompilacja wieloprocesorów**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`do kompilacji użyj wielu procesorów. Ten parametr tworzy proces dla każdego skutecznego procesora na komputerze.

   Aby uzyskać więcej informacji, zobacz [/MP (Kompilacja z wieloma procesami)](/cpp/build/reference/mp-build-with-multiple-processes). Zobacz też **ProcessorNumber** parametr w tej tabeli.

- **Nazwa pliku objectfile**

   Opcjonalny parametr **String.**

   Określa nazwę pliku lub katalog obiektu (obj), który ma być używany zamiast domyślnego.

   Aby uzyskać więcej informacji, zobacz [/Fo (nazwa pliku obiektu)](/cpp/build/reference/fo-object-file-name).

- **Pliki obiektów**

   Parametr **Opcjonalny ciąg[].**

   Lista plików obiektów.

- **Nazwa OmitDefaultLibName**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, pomija domyślną nazwę biblioteki wykonywania C z pliku obiektu (*.obj*). Domyślnie kompilator umieszcza nazwę biblioteki w pliku *obj,* aby skierować konsolidator do właściwej biblioteki.

   Aby uzyskać więcej informacji, zobacz [/Zl (Pomiń domyślną nazwę biblioteki).](/cpp/build/reference/zl-omit-default-library-name)

- **OmitFramePointers (OmitFramePointers)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program ,pomija tworzenie wskaźników ramki na stosie wywołań.

   Aby uzyskać więcej informacji, zobacz [/Oy (Pominięcie wskaźnika klatki)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, powoduje kompilator do przetwarzania klauzul OpenMP i dyrektyw.

   Aby uzyskać więcej informacji, zobacz [/openmp (Enable OpenMP 2.0 support)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optymalizacji**

   Opcjonalny parametr **String.**

   Określa różne optymalizacje kodu dla szybkości i rozmiaru.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Wyłączone** - **/Od**

  - **MinSpace** - **/O1**

  - **MaxSpeed** - **/O2**

  - **Pełna** - **/Wół**

    Aby uzyskać więcej informacji, zobacz [/O Options (Optimize code)](/cpp/build/reference/o-options-optimize-code).

- **Wstępnie skompilowanyheader**

   Opcjonalny parametr **String.**

   Utwórz lub użyj wstępnie skompilowanego pliku nagłówka (*pch*) podczas kompilacji.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NotUj** - *\<brak>*

  - **Tworzenie** - **/Yc**

  - **Użyj** - **/Yu**

    Aby uzyskać więcej informacji, zobacz [/Yc (Tworzenie wstępnie skompilowanego pliku nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Użyj wstępnie skompilowanego pliku nagłówka)](/cpp/build/reference/yu-use-precompiled-header-file). Zobacz także **parametry PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** w tej tabeli.

- **Wstępnie skompilowany plikheader**

   Opcjonalny parametr **String.**

   Określa wstępnie skompilowany plik nagłówka do utworzenia lub użycia.

   Aby uzyskać więcej informacji, zobacz [/Yc (Tworzenie wstępnie skompilowanego pliku nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Użyj wstępnie skompilowanego pliku nagłówka)](/cpp/build/reference/yu-use-precompiled-header-file).

- **Wstępnie skompilowany plik nagłówków**

   Opcjonalny parametr **String.**

   Określa nazwę ścieżki dla wstępnie skompilowanego nagłówka zamiast domyślnej nazwy ścieżki.

   Aby uzyskać więcej informacji, zobacz [/Fp (Nazwa pliku pch)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments (Przetwarzanie wstępne)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, zachowuje komentarze podczas wstępnego przetwarzania.

   Aby uzyskać więcej informacji, zobacz [/C (Zachowywanie komentarzy podczas wstępnego przetwarzania)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **Definicje przedtwarze**

   Parametr `String[]` opcjonalny.

   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.

   Aby uzyskać więcej informacji, zobacz [/D (Definicje preprocesora)](/cpp/build/reference/d-preprocessor-definitions).

- **Przetwory wstępneOutput**

   Parametr `ITaskItem[]` opcjonalny.

   Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.

- **Ścieżka wstępnaOutputPath**

   Parametr `String` opcjonalny.

   Określa nazwę pliku wyjściowego, do którego parametr **PreprocessToFile** zapisuje wstępnie przetworzone dane wyjściowe.

   Aby uzyskać więcej informacji, zobacz [/Fi (Nazwa pliku wyjściowego przetwarzania wstępnego).](/cpp/build/reference/fi-preprocess-output-file-name)

- **Numery wstępneSuppressLineNumbers**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program przetworzy pliki źródłowe języka C i C++ i skopiuje wstępnie przetworzone pliki do standardowego urządzenia wyjściowego.

   Aby uzyskać więcej informacji, zobacz [/EP (Preprocess do stdout bez dyrektyw #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **Plik wstępny**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, wstępnie przetworzy pliki źródłowe C i C++ i zapisuje wstępnie przetworzone dane wyjściowe do pliku.

   Aby uzyskać więcej informacji, zobacz [/P (Preprocess do pliku)](/cpp/build/reference/p-preprocess-to-a-file).

- **Numer procesora**

   Parametr `Integer` opcjonalny.

   Określa maksymalną liczbę procesorów do użycia w kompilacji wieloprocesorowej. Tego parametru należy używać w połączeniu z parametrem **MultiProcessorCompilation.**

- **Nazwa pliku programuDataBaseFile**

   Parametr `String` opcjonalny.

   Określa nazwę pliku bazy danych programu (PDB).

   Aby uzyskać więcej informacji, zobacz [/Fd (Nazwa pliku bazy danych programu).](/cpp/build/reference/fd-program-database-file-name)

- **Biblioteka uruchomieniowa**

   Parametr `String` opcjonalny.

   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL i wybiera wersje detaliczne lub debugowania biblioteki wyłowionej.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Wielowątkowe** - **/MT**

  - **WielowątkoweDebug** - **/MTd**

  - **MultiThreadedDLL** - **/MD**

  - **MultiThreadedDebugDLL** - **/MDd**

    Aby uzyskać więcej informacji, zobacz [/MD, /MT, /LD (Użyj biblioteki czasu wykonywania)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **Środowisko wykonawczeTypeInfo**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, dodaje kod, aby sprawdzić typy obiektów C++ w czasie wykonywania (informacje o typie czasu wykonywania).

   Aby uzyskać więcej informacji, zobacz [/GR (Włącz informacje o typie czasu wykonywania)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes (w tym)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, powoduje, że kompilator do wysuń listę plików dołączanych.

   Aby uzyskać więcej informacji, zobacz [/showIncludes (Lista plików dołącza)](/cpp/build/reference/showincludes-list-include-files).

- **Mniejszy TypCheck**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`raportuje błąd czasu wykonywania, jeśli wartość jest przypisana do mniejszego typu danych i powoduje utratę danych.

   Aby uzyskać więcej informacji, zobacz **/RTCc** opcja w [/RTC (Sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).

- **Źródeł**

   Wymagany parametr interfejsu `ITaskItem[]`.

   Określa listę plików źródłowych oddzielonych spacjami.

- **Buforowanie ciągów**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, umożliwia kompilatorowi utworzyć jedną kopię identycznych ciągów w obrazie programu.

   Aby uzyskać więcej informacji, zobacz [/GF (Wyeliminuj zduplikowane ciągi)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **Wyrównanie członków struct**

   Parametr `String` opcjonalny.

   Określa wyrównanie bajtów dla wszystkich elementów członkowskich w strukturze.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Domyślnie** - **/Zp1**

  - **1Djówka** - **/Zp1**

  - **2Dejbyty** - **/Zp2**

  - **4Bajty** - **/Zp4**

  - **8Bajty** - **/Zp8**

  - **16 Bajtów** - **/Zp16**

    Aby uzyskać więcej informacji, zobacz [/Zp (Wyrównanie elementu członkowskiego struktury)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner (SuppressStartupBanner)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.

   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijanie banera startowego) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory (TrackerLogDirectory)**

   Parametr `String` opcjonalny.

   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametry w tej tabeli.

- **TreatSpecificWarningsAsErrors**

   Parametr **Opcjonalny ciąg[].**

   Traktuje określoną listę ostrzeżeń kompilatora jako błędy.

   Aby uzyskać więcej informacji, zobacz **/we** `n` option in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Poziom ostrzeżenia)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, traktować wszystkie ostrzeżenia kompilatora jako błędy.

   Aby uzyskać więcej informacji, zobacz **/WX** option in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Poziom ostrzeżenia)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, `wchar_t` potraktuj typ jako typ macierzysty.

   Aby uzyskać więcej informacji, zobacz [/Zc:wchar_t (wchar_t jest typem macierzystym)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, undefines specyficzne dla firmy Microsoft symbole, które kompilator definiuje.

   Aby uzyskać więcej informacji, zobacz **/u** opcja w [/U, /u (Symbole Undefine)](/cpp/build/reference/u-u-undefine-symbols).

- **DefinePreprocessorDefinitions**

   Parametr `String[]` opcjonalny.

   Określa listę jednego lub więcej symboli preprocesora do nieobrony.

   Aby uzyskać więcej informacji, zobacz **/U** option in [/U, /u (Undefine symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **Ścieżki UseFullPaths**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, wyświetla pełną ścieżkę plików kodu źródłowego przekazanych do kompilatora w diagnostyce.

   Aby uzyskać więcej informacji, zobacz [/FC (Pełna ścieżka pliku kodu źródłowego w diagnostyce)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerNaświetlanie**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`plik wyjściowy powoduje utworzenie pliku wyjściowego w formacie UTF-8.

   Aby uzyskać więcej informacji, zobacz **/FAu** opcja w [/FA, /Fa (plik aukcji)](/cpp/build/reference/fa-fa-listing-file).

- **Warninglevel**

   Parametr `String` opcjonalny.

   Określa najwyższy poziom ostrzeżenia, który ma być generowany przez kompilator.

   Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **TurnOffAllWarnings** - **/W0**

  - **Poziom1** - **/W1**

  - **Poziom 2** - **/W2**

  - **Poziom 3** - **/W3**

  - **Poziom4** - **/W4**

  - **EnableAllWarnings** - **/Ściana**

    Aby uzyskać więcej informacji, zobacz **/W**_n_ opcja w [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /wo, /wo, /Wv, /WX (poziom ostrzeżenia).](/cpp/build/reference/compiler-option-warning-level)

- **Cała aoptymalizacja programu**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, umożliwia optymalizację całego programu.

   Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Parametr `String` opcjonalny.

   Określa nazwę wygenerowanych plików dokumentacji XML. Ten parametr może być nazwą pliku lub katalogu.

   Aby uzyskać więcej `name` informacji, zobacz argument w [/doc (Komentarze dokumentacji procesu) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz też **GenerateXMLDocumentationFiles** parametr w tej tabeli.

- **MinimalRebuildFromTracking**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`zostanie wykonana śledzona kompilacja przyrostowa; jeśli `false`zostanie przeprowadzona przebudowa.

- **TLogReadFiles**

   Parametr `ITaskItem[]` opcjonalny.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików odczytu*.

   Dziennik śledzenia plików odczytu (*.tlog*) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i jest używany przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz **Parametry TrackerLogDirectory** i **TrackFileAccess** w tej tabeli.

- **TLogWriteFiles (Pliki TLogWriteFiles)**

   Parametr `ITaskItem[]` opcjonalny.

   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików zapisu*.

   Dziennik śledzenia plików zapisu (*.tlog*) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie i jest używany przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz **Parametry TrackerLogDirectory** i **TrackFileAccess** w tej tabeli.

- **TrackFileAccess (Plik utworu)**

   Parametr `Boolean` opcjonalny.

   Jeśli `true`, śledzi wzorce dostępu do plików.

   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametry w tej tabeli.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
