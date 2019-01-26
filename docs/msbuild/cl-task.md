---
title: Cl — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e8de1edc266489a6260176e0b9e8aec8df62ba2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956704"
---
# <a name="cl-task"></a>CL — Zadanie
Narzędzia kompilatora Visual C++, jest zawijany *cl.exe*. Kompilator generuje plik wykonywalny (*.exe*) plików, biblioteka dołączana dynamicznie (*.dll*) plików lub modułu kodu (*.netmodule*) plików. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](/cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parametry  
 Na poniższej liście opisano parametry **CL** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
- **AdditionalIncludeDirectories**  
  
   Opcjonalny parametr typu String [].  
  
   Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/I (dodatkowe katalogi dołączenia)](/cpp/build/reference/i-additional-include-directories).  
  
- **AdditionalOptions**  
  
   Parametr opcjonalny ciąg.  
  
   Listę opcji wiersza polecenia. Na przykład "/\<opcja1 > /\<opcja2 > /\<opcja #>". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne parametry zadania.  
  
   Aby uzyskać więcej informacji, zobacz [opcje kompilatora](/cpp/build/reference/compiler-options).  
  
- **AdditionalUsingDirectories**

   Opcjonalny parametr typu String [].  
  
   Określa katalog, który kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików przekazywane do **#using** dyrektywy.  
  
   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](/cpp/build/reference/ai-specify-metadata-directories).  
  
- **AlwaysAppend**  
  
   Parametr opcjonalny ciąg.  
  
   Ciąg to zawsze pobiera emitowane w wierszu polecenia. Jego wartość domyślna to "**/c**".  
  
- **AssemblerListingLocation**  
  
   Tworzy plik listingu, który zawiera kod zestawu.  
  
   Aby uzyskać więcej informacji, zobacz **/Fa** opcji [/FA, /Fa (umieszczanie pliku)](/cpp/build/reference/fa-fa-listing-file).  
  
- **AssemblerOutput**  
  
   Parametr opcjonalny ciąg.  
  
   Tworzy plik listingu, który zawiera kod zestawu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NoListing** - *\<Brak >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **Wszystkie** -   **/facs**  
  
    Aby uzyskać więcej informacji, zobacz **/FA**, **/FAC**, **/FAS**, i **/facs** opcji na liście [/FA, /Fa (umieszczanie pliku)](/cpp/build/reference/fa-fa-listing-file).  
  
- **BasicRuntimeChecks**  
  
   Parametr opcjonalny ciąg.  
  
   Włącza i wyłącza funkcję Sprawdzanie błędów czasu wykonywania w połączeniu z [runtime_checks](/cpp/preprocessor/runtime-checks) pragmy.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** -                          *\<Brak >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Aby uzyskać więcej informacji, zobacz [usunęliśmy (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **BrowseInformation**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, tworzy plik informacji przeglądania.  
  
   Aby uzyskać więcej informacji, zobacz **/FR** opcji [/FR, /Fr (Utwórz plik .sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BrowseInformationFile**  
  
   Parametr opcjonalny ciąg.  
  
   Określa nazwę pliku dla pliku informacyjnego przeglądarki.  
  
   Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametru w tej tabeli, a także znaleźć [/FR, /Fr (Utwórz plik .sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
- **BufferSecurityCheck**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, wykrywa niektóre przepełnienia buforów, które zastępują adres zwrotny technikę wydobywania kod, który nie wymusza ograniczeń rozmiaru buforu.  
  
   Aby uzyskać więcej informacji, zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check).  
  
- **BuildingInIDE**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, oznacza to, że **MSBuild** jest wywoływany przez środowisko IDE. W przeciwnym razie **MSBuild** jest wywoływany w wierszu polecenia.  
  
- **CallingConvention**  
  
   Parametr opcjonalny ciąg.  
  
   Określa konwencję wywołania zamówienia w funkcji argumenty są wypychane na stosie, należy określić, czy wywołujący funkcję lub wywołana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję dekorowania nazwy, Kompilator używa do identyfikowania poszczególnych funkcji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **/Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    Aby uzyskać więcej informacji, zobacz [/Gd, / GR, / GV, /Gz (Konwencja wywoływania)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
- **CompileAs**  
  
   Parametr opcjonalny ciąg.  
  
   Określa, czy można skompilować pliku wejściowego jako plik źródłowy C lub C++.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Aby uzyskać więcej informacji, zobacz [TP, /Tp, TP, /TP (Określ typ pliku źródłowego)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
- **CompileAsManaged**  
  
   Parametr opcjonalny ciąg.  
  
   Umożliwia aplikacji i składników korzystać z funkcji z środowisko uruchomieniowe języka wspólnego (CLR).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **FALSE** - *\<Brak >*  
  
  - **true** - **/clr**  
  
  - **Czysty** -   **/CLR: pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
- **CreateHotpatchableImage**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, informuje kompilator, aby przygotować obraz dla *poprawki*. Tego parametru gwarantuje, że pierwsza instrukcja każdej funkcji jest dwubajtowa, który jest wymagany dla poprawki.  
  
   Aby uzyskać więcej informacji, zobacz [/hotpatch (Utwórz obraz hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
- **DebugInformationFormat**  
  
   Parametr opcjonalny ciąg.  
  
   Wybiera typ informacji o debugowaniu utworzonych dla programu, czy te informacje są przechowywane w obiekcie (*.obj*) plików lub w programie bazy danych (PDB).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Aby uzyskać więcej informacji, zobacz [/z7, / zi, /ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format).  
  
- **DisableLanguageExtensions**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli **true**, informuje kompilator będzie emitował błąd dotyczące konstrukcji języka, które nie są zgodne z ANSI C lub ANSI C++.  
  
   Aby uzyskać więcej informacji, zobacz **/Za** opcji [/za, /Ze (Wyłącz rozszerzenia językowe)](/cpp/build/reference/za-ze-disable-language-extensions).  
  
- **DisableSpecificWarnings**  
  
   Opcjonalny parametr typu String [].  
  
   Wyłącza numery ostrzeżeń, które są określone w liście rozdzielanej średnikami.  
  
   Aby uzyskać więcej informacji, zobacz `/wd` opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
- **EnableEnhancedInstructionSet**  
  
   Parametr opcjonalny ciąg.  
  
   Określa architekturę do generowania kodu, który używa rozszerzenia SSE (Streaming SIMD) i instrukcji Streaming SIMD Extensions 2 (SSE2).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **SSE2**  
  
    Aby uzyskać więcej informacji, zobacz [/arch (x86)](/cpp/build/reference/arch-x86).  
  
- **EnableFiberSafeOptimizations**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, obsługuje bezpieczeństwo włókien dla danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych, czyli danych przydzielonych przy użyciu `__declspec(thread)`.  
  
   Aby uzyskać więcej informacji, zobacz [/GT (Obsługa włókien magazynu wątków lokalnych)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
- **EnablePREfast**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, Włącz analizę kodu.  
  
   Aby uzyskać więcej informacji, zobacz [/ analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis).  
  
- **ErrorReporting**  
  
   Parametr opcjonalny ciąg.  
  
   Pozwala zapewnić wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft. Domyślnie to ustawienie w kompilacjach IDE **monitu** i ustawienie w kompilacji z wiersza polecenia jest **kolejki**.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **None** - **/errorReport:none**  
  
  - **Wiersz** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](/cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
- **ExceptionHandling**  
  
   Parametr opcjonalny ciąg.  
  
   Określa model obsługi wyjątków, aby używane przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **FALSE** - *\<Brak >*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątku)](/cpp/build/reference/eh-exception-handling-model).  
  
- **ExpandAttributedSource**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, tworzy plik listingu, która została rozszerzona atrybuty, które są wstrzykiwane do pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/Fx (scalania wprowadzony kod)](/cpp/build/reference/fx-merge-injected-code).  
  
- **FavorSizeOrSpeed**  
  
   Parametr opcjonalny ciąg.  
  
   Określa, czy preferować rozmiar czy prędkość kodu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Neither** - *\<none>*  
  
  - **Rozmiar** -   **/OS**  
  
  - **Szybkość** - **/Ot**  
  
    Aby uzyskać więcej informacji, zobacz [/OS, /Ot (Preferuj mały kod, Preferuj szybki kod)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
- **FloatingPointExceptions**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, umożliwia wiarygodny model wyjątków zmiennopozycyjnych. Wyjątki będą zgłaszane, natychmiast po ich wygenerowaniu.  
  
   Aby uzyskać więcej informacji, zobacz /**fp: except** opcji [/FP (określenie zachowania zmiennoprzecinkowego)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **FloatingPointModel**  
  
   Parametr opcjonalny ciąg.  
  
   Ustawia wartość zmiennoprzecinkowa punktu modelu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Dokładne** -   **/FP: precise**  
  
  - **Ścisłe** -   **/FP: strict**  
  
  - **Fast** - **/fp:fast**  
  
    Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennoprzecinkowego)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
- **ForceConformanceInForLoopScope**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, implementuje standardowego zachowania C++ w [dla](/cpp/cpp/for-statement-cpp) pętli, które należy użyć rozszerzeń firmy Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: forscope (Wymuszaj zgodność w zakresie pętli for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).  
  
- **ForcedIncludeFiles**  
  
   Opcjonalnie `String[]` parametru.  
  
   Powoduje, że preprocesor do przetworzenia jeden lub więcej plików określony nagłówek.  
  
   Aby uzyskać więcej informacji, zobacz [/FI (nazwa pliku wymuszonego dołączenia)](/cpp/build/reference/fi-name-forced-include-file).  
  
- **ForcedUsingFiles**  
  
   Opcjonalnie **String []** parametru.  
  
   Powoduje, że preprocesora aby przetworzyć jednego lub więcej określonych **#using** plików.  
  
   Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszony #using)](/cpp/build/reference/fu-name-forced-hash-using-file).  
  
- **FunctionLevelLinking**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat).  
  
   Aby uzyskać więcej informacji, zobacz [/Gy (włączenie łączenia poziomie funkcji)](/cpp/build/reference/gy-enable-function-level-linking).  
  
- **GenerateXMLDocumentationFiles**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator przetwarzanie komentarzy dokumentacji w plikach kodu źródłowego, a także tworzenie *.xdc* pliku dla każdego pliku kodu źródłowego, który ma komentarze dokumentacji.  
  
   Aby uzyskać więcej informacji, zobacz [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz też **XMLDocumentationFileName** parametru w tej tabeli.  
  
- **IgnoreStandardIncludePath**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.  
  
   Aby uzyskać więcej informacji, zobacz [/X (Ignoruj standardowe ścieżki dołączanych plików)](/cpp/build/reference/x-ignore-standard-include-paths).  
  
- **InlineFunctionExpansion**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa poziom rozwijania funkcji inline w kompilacji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **Wyłączone** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](/cpp/build/reference/ob-inline-function-expansion).  
  
- **IntrinsicFunctions**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zastępuje niektórych funkcji wywołuje z wewnętrznych lub w przeciwnym razie specjalnych formy funkcji pomagających aplikacji działają szybciej.  
  
   Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](/cpp/build/reference/oi-generate-intrinsic-functions).  
  
- **MinimalRebuild**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, włącza minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione C++ klasy definicje (przechowywane w plikach nagłówków (.h)) musi być ponownie kompilowane.  
  
   Aby uzyskać więcej informacji, zobacz [/Gm (Włącz minimalną ponowną kompilację)](/cpp/build/reference/gm-enable-minimal-rebuild).  
  
- **MultiProcessorCompilation**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, użycie wielu procesorów do skompilowania. Ten parametr tworzy proces dla każdego procesora skuteczne na komputerze.  
  
   Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](/cpp/build/reference/mp-build-with-multiple-processes). Zobacz też **ProcessorNumber** parametru w tej tabeli.  
  
- **ObjectFileName**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę pliku obiektu (.obj) lub katalog ma być używany zamiast domyślnego.  
  
   Aby uzyskać więcej informacji, zobacz [/Fo (nazwa pliku obiektu)](/cpp/build/reference/fo-object-file-name).  
  
- **ObjectFiles**  
  
   Opcjonalnie **String []** parametru.  
  
   Lista plików obiektów.  
  
- **OmitDefaultLibName**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, pomija domyślną nazwę biblioteki wykonawczej języka C z obiektu (*.obj*) pliku. Domyślnie kompilator umieszcza nazwę biblioteki do *.obj* pliku do kierowania konsolidator odpowiedniej biblioteki.  
  
   Aby uzyskać więcej informacji, zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](/cpp/build/reference/zl-omit-default-library-name).  
  
- **OmitFramePointers**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, pomija tworzenie wskaźników ramek na stosie wywołań.  
  
   Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](/cpp/build/reference/oy-frame-pointer-omission).  
  
- **OpenMPSupport**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator przetwarzania klauzule OpenMP i dyrektywy.  
  
   Aby uzyskać więcej informacji, zobacz [/OpenMP (Włącz OpenMP 2.0 obsługę)](/cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
- **Optymalizacja**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa różne optymalizacje kodu szybkości i rozmiaru.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wyłączone** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** -   **/O2**  
  
  - **Full** - **/Ox**  
  
    Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code).  
  
- **PrecompiledHeader**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Utwórz lub użyj prekompilowanego nagłówka (*.pch*) pliku podczas kompilacji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotUsing** - *\<Brak >*  
  
  - **Tworzenie** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Korzystaj z prekompilowanego pliku nagłówkowego pliku)](/cpp/build/reference/yu-use-precompiled-header-file). Zobacz też **PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** parametrów w tej tabeli.  
  
- **PrecompiledHeaderFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę prekompilowanego pliku nagłówka do utworzenia lub używania.  
  
   Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Korzystaj z prekompilowanego pliku nagłówkowego pliku)](/cpp/build/reference/yu-use-precompiled-header-file).  
  
- **PrecompiledHeaderOutputFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki.  
  
   Aby uzyskać więcej informacji, zobacz [/Fp (nazwa pliku .pch)](/cpp/build/reference/fp-name-dot-pch-file).  
  
- **PreprocessKeepComments**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zachowuje komentarze podczas przetwarzania wstępnego.  
  
   Aby uzyskać więcej informacji, zobacz [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](/cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
- **PreprocessorDefinitions**  
  
   Opcjonalnie `String[]` parametru.  
  
   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](/cpp/build/reference/d-preprocessor-definitions).  
  
- **PreprocessOutput**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów dane wyjściowe preprocesora, które może być używany i wyemitowane przez zadania.  
  
- **PreprocessOutputPath**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę pliku wyjściowego, do którego **PreprocessToFile** parametr zapisuje wstępnie przetworzone produkty wyjściowe.  
  
   Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie nazwę pliku danych wyjściowych)](/cpp/build/reference/fi-preprocess-output-file-name).  
  
- **PreprocessSuppressLineNumbers**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`wstępnie przetwarza pliki źródłowe C i C++ oraz kopiuje pliki wstępnie przetworzony do urządzenia wyjścia standardowego.  
  
   Aby uzyskać więcej informacji, zobacz [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
- **PreprocessToFile**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`wstępnie przetwarza pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](/cpp/build/reference/p-preprocess-to-a-file).  
  
- **ProcessorNumber**  
  
   Opcjonalnie `Integer` parametru.  
  
   Określa maksymalną liczbę procesorów, którą należy używać w kompilacji wieloprocesorowej. Tego parametru należy użyć w połączeniu z **MultiProcessorCompilation** parametru.  
  
- **ProgramDataBaseFileName**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę pliku dla pliku bazy danych (PDB) programu.  
  
   Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](/cpp/build/reference/fd-program-database-file-name).  
  
- **RuntimeLibrary**  
  
   Opcjonalnie `String` parametru.  
  
   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL i wybiera sprzedaży detalicznej lub debugowania wersji biblioteki wykonawczej.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](/cpp/build/reference/md-mt-ld-use-run-time-library).  
  
- **RuntimeTypeInfo**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje typu run-time).  
  
   Aby uzyskać więcej informacji, zobacz [/GR (Włącz informacje typu run-time)](/cpp/build/reference/gr-enable-run-time-type-information).  
  
- **ShowIncludes**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator danych wyjściowych listy plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/showincludes (Wymień pliki dołączane)](/cpp/build/reference/showincludes-list-include-files).  
  
- **SmallerTypeCheck**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zgłasza błąd w czasie wykonywania, jeśli wartość jest przypisana do mniejszych typów danych i powoduje utratę danych.  
  
   Aby uzyskać więcej informacji, zobacz **/RTCc** opcji [usunęliśmy (sprawdzanie błędów czasu wykonywania)](/cpp/build/reference/rtc-run-time-error-checks).  
  
- **Źródła**  
  
   Wymagane `ITaskItem[]` parametru.  
  
   Określa listę plików źródłowych, rozdzielone spacjami.  
  
- **StringPooling**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, umożliwia kompilatorowi tworzenie po jednej kopii identycznych ciągów w obrazie programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GF (wyeliminować ciągów zduplikowanych)](/cpp/build/reference/gf-eliminate-duplicate-strings).  
  
- **StructMemberAlignment**  
  
   Opcjonalnie `String` parametru.  
  
   Określa bajtowe wyrównanie dla wszystkich członków w strukturze.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie członka struktury)](/cpp/build/reference/zp-struct-member-alignment).  
  
- **SuppressStartupBanner**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.  
  
   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
- **TrackerLogDirectory**  
  
   Opcjonalnie `String` parametru.  
  
   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.  
  
   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametrów w tej tabeli.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Opcjonalnie **String []** parametru.  
  
   Traktuje określona lista ostrzeżenia kompilatora jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/we** `n` opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWarningAsError**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, traktuje wszystkie ostrzeżenia kompilatora jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/WX** opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, Traktuj `wchar_t` typu jako typu natywnego.  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: (wchar_t wchar_t jest typem natywnym)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, jedno anulowanie definicji symboli specyficzne dla firmy Microsoft, które definiuje kompilator.  
  
   Aby uzyskać więcej informacji, zobacz **/u** opcji [/U, /u (Niezdefiniowany symbole)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UndefinePreprocessorDefinitions**  
  
   Opcjonalnie `String[]` parametru.  
  
   Określa listę jednego lub wielu symboli preprocesora usunięcia definicji.  
  
   Aby uzyskać więcej informacji, zobacz **/U** opcji [/U, /u (Niezdefiniowany symbole)](/cpp/build/reference/u-u-undefine-symbols).  
  
- **UseFullPaths**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, wyświetla pełną ścieżkę plików kodu źródłowego przekazane do kompilatora w diagnostyce.  
  
   Aby uzyskać więcej informacji, zobacz [/FC (pełna ścieżka pliku kodu źródłowego w diagnostyce)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
- **UseUnicodeForAssemblerListing**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że plik wyjściowy będzie utworzony w formacie UTF-8.  
  
   Aby uzyskać więcej informacji, zobacz **/fau** opcji [/FA, /Fa (umieszczanie pliku)](/cpp/build/reference/fa-fa-listing-file).  
  
- **Poziom_ostrzeżeń**  
  
   Opcjonalnie `String` parametru.  
  
   Określa najwyższy poziom ostrzeżenia, który ma zostać wygenerowane przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** -   **/Wall**  
  
    Aby uzyskać więcej informacji, zobacz **Wn**_n_ opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
- **WholeProgramOptimization**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, włącza optymalizację całego programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GL (optymalizacja całego programu)](/cpp/build/reference/gl-whole-program-optimization).  
  
- **XMLDocumentationFileName**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę wygenerowanego pliki dokumentacji XML. Ten parametr może być nazwa pliku lub katalogu.  
  
   Aby uzyskać więcej informacji, zobacz `name` argument [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz też **GenerateXMLDocumentationFiles** parametru w tej tabeli.  
  
- **MinimalRebuildFromTracking**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, śledzonych kompilacja przyrostowa odbywa się; Jeśli `false`, ponownej kompilacji jest wykonywane.  
  
- **TLogReadFiles**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów, które reprezentują *odczytać pliku dzienniki śledzenia*.  
  
   Śledzenie odczytu pliku dziennika (*.tlog*) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i jest używana przez system kompilacji projektu do obsługi kompilacje przyrostowe. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **element TrackFileAccess** parametrów w tej tabeli.  
  
- **TLogWriteFiles**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów, które reprezentują *wpisywanie do pliku tekstowego dzienniki śledzenia*.  
  
   Dziennika śledzenia pliku zapisu (*.tlog*) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie i jest używana przez system kompilacji projektu do obsługi kompilacje przyrostowe. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **element TrackFileAccess** parametrów w tej tabeli.  
  
- **TrackFileAccess**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, śledzi wzorce dostępu do pliku.  
  
   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametrów w tej tabeli.  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)