---
title: Zadanie ClangCompile | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), ClangCompile task
- ClangCompile task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 218ef07fa3b086a2240362011067bf526088d1f4
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515314"
---
# <a name="clangcompile-task"></a>Zadanie ClangCompile

Narzędzia kompilatora Visual C++, jest zawijany clang.exe.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **ClangCompile** zadania.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalnie **string []** parametru.<br/><br/>Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna.<br/><br/>Użyj `-I[path]`.|
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.|
|**BufferSecurityCheck**|Opcjonalnie **ciąg** parametru.<br/><br/>Kontrola zabezpieczeń pomaga wykryć stosu przepełnień buforu, typowy atak na zabezpieczenia programu. <br/><br/>Użyj `fstack-protector`.|
|**BuildingInIde**|Opcjonalnie **bool** parametru.|
|**CLanguageStandard**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa standard języka C.<br/><br/>Użyj `std=[value]` wartością **c89**, **c99**, **c11**, **gnu99**, lub **gnu11**.|
|**ClangVersion**|Opcjonalnie **ciąg** parametru.|
|**CompileAs**|Opcjonalnie **ciąg** parametru.<br/><br/>Wybierz opcję języka kompilowania dla plików .c i .cpp. Domyślne wykryje na podstawie rozszerzenia c lub CPP rozszerzenie.<br/><br/>Użyj `-x c`, `-x c++`.|
|**CppLanguageStandard**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa standard języka C++.<br/><br/>Użyj `std=[value]` o wartości **c ++ 98**, **c ++ 11**, **1y c ++**, **gnu ++ 98**, **gnu c++ 11**, lub **gnu ++ 1y**.|
|**DataLevelLinking**|Opcjonalnie **bool** parametru.<br/><br/>Umożliwia optymalizacjom konsolidatora usuwanie nieużywanych danych przez emitowanie każdego elementu danych w osobnej sekcji.|
|**DebugInformationFormat**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa typ informacji o debugowaniu generowanych przez kompilator.<br/><br/>**Brak**, tworzy żadnych informacji debugowania, dlatego kompilacji może być szybsze (Użyj `g0`).<br/>**FullDebug**, Generuj informacje debugowania DWARF2 (Użyj `g2 -gdwarf-2`).<br/>**Numer wiersza**, Generuj tylko informacje o numerze wiersza (Użyj `gline-tables-only`).|
|**EnableNeonCodegen**|Opcjonalnie **bool** parametru.<br/><br/>Umożliwia generowanie kodu dla sprzętu zmiennoprzecinkowego NEON. Dotyczy tylko architektury arm.|
|**ExceptionHandling**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa model obsługi wyjątków, aby używane przez kompilator.<br/><br/>**Wyłączone**, wyłącz obsługę wyjątków (Użyj `fno-exceptions`).<br/>**Włączone**, Włącz obsługę wyjątków (Użyj `fexceptions`).<br/>**UnwindTables**, generuje wszelkie wymagane dane statyczne, ale nie ma wpływu na wygenerowany kod (Użyj `funwind-tables`).|
|**FloatABI**|Opcjonalnie **ciąg** parametru.<br/><br/>Opcja umożliwiająca wybranie zmiennoprzecinkowego interfejsu ABI.<br/><br/>**elastyczne**, powoduje, że kompilatorowi Generowanie danych wyjściowych zawierających wywołania bibliotek dotyczące operacji zmiennoprzecinkowych (Użyj `mfloat-abi=soft`).<br/>**softfp**, umożliwia generowanie kodu przy użyciu instrukcji zmiennoprzecinkowych sprzętu, ale nadal używa konwencji wywoływania zmiennoprzecinkowych (Użyj `mfloat-abi=softfp`).<br/>**twarde**umożliwia generowanie instrukcji zmiennoprzecinkowych i używa konwencji wywoływania specyficznych dla operacji FPU (Użyj `mfloat-abi=hard`).|
|**ForcedIncludeFiles**|Opcjonalnie **string []** parametru.<br/><br/>co najmniej jeden wymuszony plik dyrektywy dołączyć pliki.<br/><br/>Użyj `-include [name]`.|
|**FunctionLevelLinking**|Opcjonalnie **bool** parametru.<br/><br/>Umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat). Wymagane do edycji i kontynuować pracę.<br/><br/>Użyj `ffunction-sections`.|
|**GccToolChain**|Opcjonalnie **ciąg** parametru.<br/><br/>Ścieżka folderu do łańcucha narzędzia Gcc.|
|**GNUMode**|Opcjonalnie **bool** parametru.<br/><br/>|
|**MSCompatibility**|Opcjonalnie **bool** parametru.<br/><br/>Włącz pełną zgodność języka Microsoft Visual C++.|
|**MSCompatibilityVersion**|Opcjonalnie **ciąg** parametru.<br/><br/>Wartość oddzielona reprezentujący numer wersji kompilatora firmy Microsoft do zgłoszenia w elemencie _MSC_VER (0 = nie Definiuj (domyślnie)).|
|**MSExtensions**|Opcjonalnie **bool** parametru.<br/><br/>Zaakceptuj niektóre niestandardowe konstrukcje obsługiwane przez kompilatora firmy Microsoft.|
|**MSCompilerVersion**|Opcjonalnie **ciąg** parametru.<br/><br/>Numer wersji kompilatora firmy Microsoft do zgłoszenia w elemencie _MSC_VER (0 = nie Definiuj (domyślnie)).|
|**MSVCErrorReport**|Opcjonalnie **bool** parametru.<br/><br/>Raportowanie błędów, których można użyć programu Visual Studio, można przeanalizować pliku i wierszu informacji.|
|**ObjectFileName**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę do zastąpienia domyślnej nazwy pliku obiektu; może być nazwą pliku lub katalogu.<br/><br/>Użyj `/Fo[name]`.|
|**OmitFramePointers**|Opcjonalnie **bool** parametru.<br/><br/>Pomija tworzenie wskaźników ramek na stosie wywołań.|
|**Optymalizacja**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa poziom optymalizacji aplikacji.<br/><br/>**Niestandardowe**, niestandardowa Optymalizacja.<br/>**Wyłączone**, wyłącz optymalizację (Użyj `O0`).<br/>**MinSize**, Optymalizuj pod kątem rozmiaru (Użyj `Os`).<br/>**MaxSpeed**, Optymalizuj pod kątem szybkości (Użyj `O2`).<br/>**Pełne**, kosztowne optymalizacje (Użyj `O3`).|
|**PositionIndependentCode**|Opcjonalnie **bool** parametru.<br/><br/>Generowanie niezależnie od kodu położenia (PIC) do użycia w bibliotece udostępnionej.|
|**PrecompiledHeader**|Opcjonalnie **ciąg** parametru.<br/><br/>Umożliwia utworzenie lub użycie prekompilowanego nagłówka podczas kompilacji.|
|**PrecompiledHeaderFile**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę pliku do użycia dla prekompilowanego pliku nagłówkowego. Ten plik zostanie też dodany do **wymuszone pliki dyrektywy Include** podczas kompilacji.|
|**PrecompiledHeaderOutputFileDirectory**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa katalog wygenerowanego prekompilowanego pliku nagłówkowego. Ten katalog zostanie też dodany do **dodatkowe katalogi dołączenia** podczas kompilacji.|
|**PrecompiledHeaderCompileAs**|Opcjonalnie **ciąg** parametru.<br/><br/>Wybierz opcję języka kompilowania dla prekompilowanego pliku nagłówkowego.<br/><br/>Użyj `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Opcjonalnie **string []** parametru.<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.<br/><br/>Użyj `-D`.|
|**RuntimeLibrary**|Opcjonalnie **ciąg** parametru.<br/><br/>Określ bibliotekę środowiska uruchomieniowego do konsolidacji.<br/><br/>Użyj `MSVC /MT`, `/MTd`, `/MD`, `/MDd` przełączników.<br/><br/>**Wielowątkowe**, powoduje, że aplikacja użyć statycznej, wielowątkowej wersji biblioteki wykonawczej.<br/>**MultiThreadedDebug**, definiuje _DEBUG i _MT. Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.<br/>**MultiThreadedDLL**, powoduje, że aplikacja korzysta specyficznych dla wielowątkowości i biblioteki DLL wersji biblioteki wykonawczej. Definiuje _MT i _DLL i powoduje, że kompilator umieszcza nazwę biblioteki MSVCRT.lib w pliku .obj.<br/>**MultiThreadedDebugDLL**definiuje _DEBUG, _MT i _DLL i powoduje, że aplikacja Użyj wersji biblioteki wykonawczej debugowania specyficznych dla wielowątkowości i biblioteki DLL. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|
|**RuntimeTypeInfo**|Opcjonalnie **bool** parametru.<br/><br/>Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).<br/><br/>Użyj `frtti`, `fno-rtti`.|
|**ShowIncludes**|Opcjonalnie **bool** parametru.<br/><br/>Generuje listę załączonych plików z danych wyjściowych kompilatora.<br/><br/>Użyj `-H`.|
|**Źródła**|Wymagane **[] ITaskItem** parametru.|
|**StrictAliasing**|Opcjonalnie **bool** parametru.<br/><br/>Przyjęto założenie, najbardziej rygorystyczne reguły aliasowania. Obiekt danego typu zostanie nigdy nie być zakłada się, że znajdują się na tym samym adresem co obiekt innego typu.|
|**Usuwania**|Opcjonalnie **ciąg** parametru.<br/><br/>Ścieżka folderu do katalogu głównego nagłówków i bibliotek.|
|**TargetArch**|Opcjonalnie **ciąg** parametru.<br/><br/>Architektura docelowa.|
|**ThumbMode**|Opcjonalnie **ciąg** parametru.<br/><br/>Generuj kod wykonujący dla mikroarchitektury thumb. Dotyczy tylko architektury arm.<br/><br/>**Thumb**, Generuj kod Thumb (Użyj `mthumb`).<br/>**ARM**, Generuj kod Arm (Użyj `marm`).<br/>**Wyłączone**, opcja nie dotyczy wybranej platformy.|
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br/><br/>Katalog dziennika śledzenia.|
|**TreatWarningAsError**|Opcjonalnie **bool** parametru.<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>Dla nowego projektu może być najlepiej użyć `/WX` we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą liczbą wad możliwe kodu twardych do znalezienia.|
|**UndefinePreprocessorDefinitions**|Opcjonalnie **string []** parametru.<br/><br/>Określa, że jedno anulowanie definicji preprocesora jeden lub więcej.<br/><br/>Użyj `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Opcjonalnie **bool** parametru.<br/><br/>Usuń definicje wszystkich zdefiniowanych wcześniej wartości preprocesora.<br/><br/>Użyj `-undef`.|
|**UseMultiToolTask**|Opcjonalnie **bool** parametru.<br/><br/>Kompilacja wieloprocesorowa.|
|**UseShortEnums**|Opcjonalnie **bool** parametru.<br/><br/>Typ wyliczenia używa tylko liczby bajtów wymaganej przez wejściowy zestaw możliwych wartości.|
|**pełne**|Opcjonalnie **bool** parametru.<br/><br/>Pokaż polecenia umożliwiające uruchomienie i użycie pełnych danych wyjściowych.|
|**Poziom_ostrzeżeń**|Opcjonalnie **ciąg** parametru.<br/><br/>Wybierz jak ścisły kompilator o błędów kodu. Inne flagi, które powinny zostać dodane bezpośrednio do **dodatkowe opcje** (se `/w`, `/Weverything`).<br/><br/>**TurnOffAllWarnings**, wyłącza wszystkie ostrzeżenia kompilatora (Użyj `w`).<br/>**EnableAllWarnings**, włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone (Użyj `Wall`).|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)