---
title: Zadanie clangcompile | Dokumenty firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275466"
---
# <a name="clangcompile-task"></a>Zadanie ClangCompile

Zawija narzędzie kompilatora Microsoft C++, clang.exe.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **ClangCompile.**

|Parametr|Opis|
|---------------|-----------------|
|**DodatkoweInobserwająKatary**|Opcjonalny **parametr string[].**<br/><br/>Określa jeden lub więcej katalogów do dodania do ścieżki dołączania; od siebie średnikami, jeśli więcej niż jeden.<br/><br/>Użyj witryny `-I[path]`.|
|**Dodatkoweopcje**|Opcjonalny parametr **ciągu.**|
|**Sprawdzanie zabezpieczeń bufora**|Opcjonalny parametr **ciągu.**<br/><br/>Sprawdzanie zabezpieczeń pomaga wykryć over-runs buforu stosu, typowy atak na zabezpieczenia programu. <br/><br/>Użyj witryny `fstack-protector`.|
|**BuildingInIde (Ekwid.**|Opcjonalny parametr **bool.**|
|**CLanguageStandard**|Opcjonalny parametr **ciągu.**<br/><br/>Określa standard języka C.<br/><br/>Stosować `std=[value]` z wartością **c89**, **c99**, **c11**, **gnu99**lub **gnu11**.|
|**ClangVersion (Wersja clangowa)**|Opcjonalny parametr **ciągu.**|
|**KompilacjeA**|Opcjonalny parametr **ciągu.**<br/><br/>Wybierz opcję języka kompilacji dla plików c i cpp. Wartość domyślna zostanie wykryta na podstawie zakresu .c lub .cpp.<br/><br/>Użyj `-x c` `-x c++`, .|
|**CppLanguageStandard**|Opcjonalny parametr **ciągu.**<br/><br/>Określa standard języka C++.<br/><br/>Używaj `std=[value]` z wartością **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11**lub **gnu++1y**.|
|**DataLevelLinking (Łączenie danych)**|Opcjonalny parametr **bool.**<br/><br/>Umożliwia optymalizacje konsolidatora, aby usunąć nieużywane dane, emitując każdy element danych w osobnej sekcji.|
|**DebugInformationFormat**|Opcjonalny parametr **ciągu.**<br/><br/>Określa typ informacji debugowania generowanych przez kompilator.<br/><br/>**Brak**, nie generuje żadnych informacji debugowania, więc `g0`kompilacja może być szybsza (użycie ).<br/>**FullDebug**, generowanie informacji debugowania DWARF2 (użyj `g2 -gdwarf-2`).<br/>**Liczba linii**, wygeneruj `gline-tables-only`tylko informacje o numerze wiersza (użyj ).|
|**EnableNeonCodegen (Włącz Kodowanie)**|Opcjonalny parametr **bool.**<br/><br/>Umożliwia generowanie kodu dla sprzętu zmiennoprzecinkowego NEON. Dotyczy to tylko architektury ramienia.|
|**Obsługa wyjątków**|Opcjonalny parametr **ciągu.**<br/><br/>Określa model obsługi wyjątków, który ma być używany przez kompilator.<br/><br/>**Wyłączone**, wyłącz obsługę `fno-exceptions`wyjątków (użyj ).<br/>**Włączono**, włącz obsługę `fexceptions`wyjątków (użyj ).<br/>**UnwindTables**, generuje wszelkie potrzebne dane statyczne, ale nie `funwind-tables`wpływa na kod wygenerowany (use ).|
|**Spławik**|Opcjonalny parametr **ciągu.**<br/><br/>Opcja wyboru, aby wybrać zmiennoprzecinkową ABI.<br/><br/>**soft**, powoduje, że kompilator generuje dane wyjściowe `mfloat-abi=soft`zawierające wywołania biblioteki dla operacji zmiennoprzecinkowych (użyj ).<br/>**softfp**, umożliwia generowanie kodu za pomocą sprzętowych instrukcji zmiennoprzecinkowych, `mfloat-abi=softfp`ale nadal używa soft-float konwencji wywoływania (użytkowania).<br/>**hard**, umożliwia generowanie instrukcji zmiennoprzecinkowych i wykorzystuje `mfloat-abi=hard`specyficzne dla FPU konwencje wywoływania (użytkowanie).|
|**Wymuszonewłącza pliki**|Opcjonalny **parametr string[].**<br/><br/>Jeden lub więcej wymuszonych plików dołączania.<br/><br/>Użyj witryny `-include [name]`.|
|**FunctionLevelLinking (FunkcjaPoziomowanie łączące)**|Opcjonalny parametr **bool.**<br/><br/>Umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDATs). Wymagane do edycji i kontynuowania pracy.<br/><br/>Użyj witryny `ffunction-sections`.|
|**GccToolChain (GccToolChain)**|Opcjonalny parametr **ciągu.**<br/><br/>Ścieżka folderu do łańcucha narzędzi Gcc.|
|**Tryb GNU**|Opcjonalny parametr **bool.**<br/><br/>|
|**Zgodność z MS**|Opcjonalny parametr **bool.**<br/><br/>Włącz pełną zgodność z programem Microsoft C++.|
|**MsCompatibilityVersion**|Opcjonalny parametr **ciągu.**<br/><br/>Wartość oddzielona kropkami reprezentująca numer wersji kompilatora firmy Microsoft do raportowania w _MSC_VER (0 = nie definiuj go (domyślnie)).|
|**MSWysokiecje**|Opcjonalny parametr **bool.**<br/><br/>Zaakceptuj niektóre niestandardowe konstrukcje obsługiwane przez kompilator firmy Microsoft.|
|**MSCompilerVersion (Niespołeczeństwo)**|Opcjonalny parametr **ciągu.**<br/><br/>Numer wersji kompilatora firmy Microsoft do raportowania w _MSC_VER (0 = nie definiuj go (domyślnie)).|
|**MSVCErrorZdnik**|Opcjonalny parametr **bool.**<br/><br/>Zgłaszaj błędy, których program Visual Studio może używać do analizować informacje o plikach i wierszach.|
|**Nazwa pliku objectfile**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę, która ma zastąpić domyślną nazwę pliku obiektu; może to być nazwa pliku lub katalogu.<br/><br/>Użyj witryny `/Fo[name]`.|
|**OmitFramePointers (OmitFramePointers)**|Opcjonalny parametr **bool.**<br/><br/>Pomija tworzenie wskaźników ramek na stosie wywołań.|
|**Optymalizacji**|Opcjonalny parametr **ciągu.**<br/><br/>Określa poziom optymalizacji dla aplikacji.<br/><br/>**Niestandardowa,** niestandardowa optymalizacja.<br/>**Wyłączone**, wyłączyć `O0`optymalizację (użyj ).<br/>**MinSize**, optymalizacja pod `Os`kątem rozmiaru (użyj).<br/>**MaxSpeed**, optymalizacja pod `O2`kątem prędkości (zastosowanie).<br/>**Pełna,** kosztowna optymalizacja (użytkowanie). `O3`|
|**Kod pozycyjnyzależny**|Opcjonalny parametr **bool.**<br/><br/>Generowanie kodu niezależnego pozycjonu (PIC) do użycia w bibliotece udostępnionej.|
|**Wstępnie skompilowanyheader**|Opcjonalny parametr **ciągu.**<br/><br/>Umożliwia tworzenie lub używanie wstępnie skompilowanego nagłówka podczas kompilacji.|
|**Wstępnie skompilowany plikheader**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę pliku nagłówka, który ma być używany dla wstępnie skompilowanego pliku nagłówka. Ten plik zostanie również dodany do **wymuszonych plików dołączania** podczas kompilacji.|
|**PrekompilowanyDirectorPozycji Nagłówków**|Opcjonalny parametr **ciągu.**<br/><br/>Określa katalog wygenerowanego nagłówka wstępnie skompilowanego. Ten katalog zostanie również dodany do **dodatkowych katalogów dołączania** podczas kompilacji.|
|**Wstępnie skompilowanefirmyheaderów**|Opcjonalny parametr **ciągu.**<br/><br/>Wybierz opcję języka kompilacji dla wstępnie skompilowanego pliku nagłówka.<br/><br/>Użyj `-x c-header` `-x c++-header`, .|
|**Definicje przedtwarze**|Opcjonalny **parametr string[].**<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.<br/><br/>Użyj witryny `-D`.|
|**Biblioteka uruchomieniowa**|Opcjonalny parametr **ciągu.**<br/><br/>Określ bibliotekę środowiska uruchomieniowego do łączenia.<br/><br/>Użyj `MSVC /MT` `/MTd`, `/MD` `/MDd` , przełączników.<br/><br/>**MultiThreaded**, powoduje, że aplikacja do korzystania z wielowątkową, statyczną wersję biblioteki w czasie wykonywania.<br/>**MultiThreadedDebug**, definiuje _DEBUG i _MT. Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.<br/>**MultiThreadedDLL**, powoduje, że aplikacja do korzystania z wielu wątłych i DLL specyficzne wersji biblioteki w czasie wykonywania. Definiuje _MT i _DLL i powoduje, że kompilator umieszcza nazwę biblioteki MSVCRT.lib w pliku obj.<br/>**MultiThreadedDebugDLL**, definiuje _DEBUG, _MT i _DLL i powoduje, że aplikacja do korzystania z debugowania wielowątkowej i DLL specyficznej wersji biblioteki w czasie wykonywania. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|
|**Środowisko wykonawczeTypeInfo**|Opcjonalny parametr **bool.**<br/><br/>Dodaje kod do sprawdzania typów obiektów języka C++ w czasie wykonywania (informacje o typie środowiska wykonawczego).<br/><br/>Użyj `frtti` `fno-rtti`, .|
|**ShowIncludes (w tym)**|Opcjonalny parametr **bool.**<br/><br/>Generuje listę plików dołączanych z wyjściem kompilatora.<br/><br/>Użyj witryny `-H`.|
|**Źródeł**|Wymagany parametr **ITaskItem[].**|
|**Ścisłeaaliasing**|Opcjonalny parametr **bool.**<br/><br/>Załóżmy, że najsurowsze reguły aliasowania. Obiekt jednego typu nigdy nie będzie zakładany, że znajduje się pod tym samym adresem co obiekt innego typu.|
|**Sysroot ( Sysroot )**|Opcjonalny parametr **ciągu.**<br/><br/>Ścieżka folderu do katalogu głównego nagłówków i bibliotek.|
|**CelArch**|Opcjonalny parametr **ciągu.**<br/><br/>Architektura docelowa.|
|**Tryb kciuka**|Opcjonalny parametr **ciągu.**<br/><br/>Generowanie kodu, który wykonuje dla mikroarchitektury kciuka. Dotyczy to tylko architektury ramienia.<br/><br/>**Thumb**, wygeneruj kod kciuka (użyj). `mthumb`<br/>**ARM**, wygeneruj kod ramienia (użyj). `marm`<br/>**Wyłączone**, opcja nie dotyczy wybranej platformy.|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **ciągu.**<br/><br/>Katalog dzienników trackera.|
|**TreatWarningAsError**|Opcjonalny parametr **bool.**<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>W przypadku nowego projektu najlepiej jest `/WX` użyć we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni jak najmniej trudnych do znalezienia wad kodu.|
|**DefinePreprocessorDefinitions**|Opcjonalny **parametr string[].**<br/><br/>Określa co najmniej jedną niedrobnie wolną od przetwarzania preprocesora.<br/><br/>Użyj witryny `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Opcjonalny parametr **bool.**<br/><br/>Oddefiuj wszystkie uprzednio zdefiniowane wartości preprocesora.<br/><br/>Użyj witryny `-undef`.|
|**UżyjMultiToolTask**|Opcjonalny parametr **bool.**<br/><br/>Kompilacja wieloprocesorowa.|
|**UżyjShortEnums**|Opcjonalny parametr **bool.**<br/><br/>Typ wyliczenia używa tylko tyle bajtów wymaganych przez zestaw wejściowy możliwych wartości.|
|**Pełne**|Opcjonalny parametr **bool.**<br/><br/>Pokaż polecenia do uruchamiania i używania pełnych danych wyjściowych.|
|**Warninglevel**|Opcjonalny parametr **ciągu.**<br/><br/>Wybierz, jak ścisłe, że kompilator ma dotyczyć błędów kodu. Inne flagi powinny być dodawane bezpośrednio `/w`do `/Weverything` **opcji dodatkowych** (se , ).<br/><br/>**TurnOffAllWarnings**, wyłącza wszystkie ostrzeżenia `w`kompilatora (użyj ).<br/>**EnableAllWarnings**, włącza wszystkie ostrzeżenia, w `Wall`tym te wyłączone domyślnie (użyj ).|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)