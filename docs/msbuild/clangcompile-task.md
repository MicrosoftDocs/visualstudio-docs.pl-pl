---
title: ClangCompile — zadanie | Microsoft Docs
description: Opisuje przeznaczenie i parametry zadania programu MSBuild ClangCompile, które Zawija narzędzie kompilatora języka C++, clang.exe.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 63b278f322e66e6622064288d322709c51df336d
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796826"
---
# <a name="clangcompile-task"></a>ClangCompile, zadanie

Zawija narzędzie kompilatora języka Microsoft C++ clang.exe.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **ClangCompile** .

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalny parametr **String []** .<br/><br/>Określa co najmniej jeden katalog do dodania do ścieżki dołączania; Oddzielaj średnikami, jeśli więcej niż jeden.<br/><br/>Użyj polecenia `-I[path]`.|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .|
|**BufferSecurityCheck**|Opcjonalny parametr **ciągu** .<br/><br/>Kontrola zabezpieczeń pomaga wykrywać bufory stosu w trybie failover, typowy atak na zabezpieczenia programu. <br/><br/>Użyj polecenia `fstack-protector`.|
|**BuildingInIde**|Opcjonalny parametr **bool** .|
|**CLanguageStandard**|Opcjonalny parametr **ciągu** .<br/><br/>Określa standard języka C.<br/><br/>Użyj `std=[value]` wartości z **C89** , **C99** , **C11** , **gnu99** lub **gnu11** .|
|**ClangVersion**|Opcjonalny parametr **ciągu** .|
|**CompileAs**|Opcjonalny parametr **ciągu** .<br/><br/>Wybierz opcję Język kompilacji dla plików. c i. cpp. Wartość domyślna zostanie wykryta w zależności od rozmiaru. c lub. cpp.<br/><br/>Użyj `-x c` , `-x c++` .|
|**CppLanguageStandard**|Opcjonalny parametr **ciągu** .<br/><br/>Określa standard języka C++.<br/><br/>Należy używać `std=[value]` z wartością **c++ 98** , **c++ 11** , **c + + 1Y** , **GNU + + 98** , **GNU + + 11** lub **GNU + + 1Y** .|
|**DataLevelLinking**|Opcjonalny parametr **bool** .<br/><br/>Umożliwia optymalizacjom konsolidatora usuwanie nieużywanych danych przez emitowanie każdego elementu danych w osobnej sekcji.|
|**DebugInformationFormat**|Opcjonalny parametr **ciągu** .<br/><br/>Określa typ informacji o debugowaniu generowanych przez kompilator.<br/><br/>**Brak** , nie tworzy informacji o debugowaniu, dzięki czemu kompilacja może być szybsza (używać `g0` ).<br/>**FullDebug** , Generuj informacje o debugowaniu DWARF2 (Użyj `g2 -gdwarf-2` ).<br/>**LineNumber** , Generuj tylko informacje o numerze wiersza (Użyj `gline-tables-only` ).|
|**EnableNeonCodegen**|Opcjonalny parametr **bool** .<br/><br/>Włącza generowanie kodu dla sprzętu zmiennoprzecinkowego NEONu. Dotyczy to tylko architektury ARM.|
|**ExceptionHandling**|Opcjonalny parametr **ciągu** .<br/><br/>Określa model obsługi wyjątków, który ma być używany przez kompilator.<br/><br/>**Wyłączone** , Wyłącz obsługę wyjątków (Użyj `fno-exceptions` ).<br/>**Włączone** , Włącz obsługę wyjątków (Użyj `fexceptions` ).<br/>**UnwindTables** , generuje wszystkie potrzebne dane statyczne, ale nie ma wpływu na wygenerowany kod (Użyj `funwind-tables` ).|
|**FloatABI**|Opcjonalny parametr **ciągu** .<br/><br/>Opcja wyboru umożliwiająca wybranie ABI zmiennoprzecinkowego.<br/><br/>**soft** , powoduje, że kompilator generuje dane wyjściowe zawierające wywołania biblioteki dla operacji zmiennoprzecinkowych (Użyj `mfloat-abi=soft` ).<br/>**softfp** , umożliwia generowanie kodu przy użyciu instrukcji zmiennoprzecinkowych sprzętu, ale nadal używa konwencji wywoływania miękkie-zmiennoprzecinkowych (Użyj `mfloat-abi=softfp` ).<br/>**trudne** , umożliwia generowanie instrukcji zmiennoprzecinkowych i używa konwencji wywoływania specyficznych dla FPU (Użyj `mfloat-abi=hard` ).|
|**ForcedIncludeFiles**|Opcjonalny parametr **String []** .<br/><br/>Co najmniej jeden wymuszony plik dyrektywy include.<br/><br/>Użyj polecenia `-include [name]`.|
|**FunctionLevelLinking**|Opcjonalny parametr **bool** .<br/><br/>Umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT). Wymagane do edycji i kontynuowania pracy.<br/><br/>Użyj polecenia `ffunction-sections`.|
|**GccToolChain**|Opcjonalny parametr **ciągu** .<br/><br/>Ścieżka folderu do łańcucha narzędzi programu w zatoce.|
|**GNUMode**|Opcjonalny parametr **bool** .<br/><br/>|
|**MSCompatibility**|Opcjonalny parametr **bool** .<br/><br/>Włącz pełną zgodność języka Microsoft C++.|
|**MSCompatibilityVersion**|Opcjonalny parametr **ciągu** .<br/><br/>Wartość oddzielona kropką reprezentująca numer wersji kompilatora firmy Microsoft do raportowania w _MSC_VER (0 = nie określaj go (domyślnie)).|
|**MSExtensions**|Opcjonalny parametr **bool** .<br/><br/>Zaakceptuj niektóre niestandardowe konstrukcje obsługiwane przez kompilator firmy Microsoft.|
|**MSCompilerVersion**|Opcjonalny parametr **ciągu** .<br/><br/>Numer wersji kompilatora firmy Microsoft do raportowania w _MSC_VER (0 = nie określaj go (domyślnie)).|
|**MSVCErrorReport**|Opcjonalny parametr **bool** .<br/><br/>Zgłoś błędy, których program Visual Studio może użyć do analizowania informacji dotyczących plików i wierszy.|
|**ObjectFileName**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu; może to być nazwa pliku lub katalogu.<br/><br/>Użyj polecenia `/Fo[name]`.|
|**OmitFramePointers**|Opcjonalny parametr **bool** .<br/><br/>Pomija tworzenie wskaźników ramek na stosie wywołań.|
|**Optymalizacja**|Opcjonalny parametr **ciągu** .<br/><br/>Określa poziom optymalizacji aplikacji.<br/><br/>**Niestandardowa,** niestandardowa Optymalizacja.<br/>**Wyłączone** , wyłącz optymalizację (Użyj `O0` ).<br/>**MinSize** , Optymalizuj pod kątem rozmiaru (Użyj `Os` ).<br/>**MaxSpeed** , Optymalizuj pod kątem szybkości (Użyj `O2` ).<br/>**Pełne** , drogie optymalizacje (Użyj `O3` ).|
|**PositionIndependentCode**|Opcjonalny parametr **bool** .<br/><br/>Generuj kod niezależnej pozycji (PIC) do użycia w bibliotece udostępnionej.|
|**PrecompiledHeader**|Opcjonalny parametr **ciągu** .<br/><br/>Umożliwia utworzenie lub użycie prekompilowanego nagłówka podczas kompilowania.|
|**PrecompiledHeaderFile**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę pliku nagłówkowego, który ma być używany dla prekompilowanego pliku nagłówkowego. Ten plik zostanie również dodany do **wymuszonych plików dołączanych** podczas kompilacji.|
|**PrecompiledHeaderOutputFileDirectory**|Opcjonalny parametr **ciągu** .<br/><br/>Określa katalog dla wygenerowanego prekompilowanego nagłówka. Ten katalog zostanie również dodany do **dodatkowych katalogów dołączanych** podczas kompilacji.|
|**PrecompiledHeaderCompileAs**|Opcjonalny parametr **ciągu** .<br/><br/>Wybierz opcję języka kompilowania dla prekompilowanego pliku nagłówkowego.<br/><br/>Użyj `-x c-header` , `-x c++-header` .|
|**PreprocessorDefinitions**|Opcjonalny parametr **String []** .<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.<br/><br/>Użyj polecenia `-D`.|
|**RuntimeLibrary**|Opcjonalny parametr **ciągu** .<br/><br/>Określ bibliotekę środowiska uruchomieniowego do konsolidacji.<br/><br/>Użyj `MSVC /MT` , `/MTd` , `/MD` , `/MDd` przełączniki.<br/><br/>**Wielowątkowy** , powoduje, że aplikacja korzysta z wielowątkowejej, statycznej wersji biblioteki wykonawczej.<br/>**MultiThreadedDebug** , definiuje _DEBUG i _MT. Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.<br/>**MultiThreadedDLL** , powoduje, że aplikacja korzysta z biblioteki wykonawczej specyficznej dla wielowątkowej i biblioteki DLL. Definiuje _MT i _DLL i powoduje, że kompilator umieszcza nazwę biblioteki MSVCRT. lib w pliku. obj.<br/>**MultiThreadedDebugDLL** , definiuje _DEBUG, _MT i _DLL i powoduje, że aplikacja korzysta z wersji biblioteki wykonawczej wielowątkowej i z biblioteką DLL. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|
|**RuntimeTypeInfo**|Opcjonalny parametr **bool** .<br/><br/>Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).<br/><br/>Użyj `frtti` , `fno-rtti` .|
|**ShowIncludes**|Opcjonalny parametr **bool** .<br/><br/>Generuje listę plików dołączanych z danymi wyjściowymi kompilatora.<br/><br/>Użyj polecenia `-H`.|
|**Źródeł**|Wymagany parametr **ITaskItem []** .|
|**StrictAliasing**|Opcjonalny parametr **bool** .<br/><br/>Przyjęto założenie rygorystycznych reguł aliasów. Obiekt jednego typu nigdy nie zostanie przyjęty, aby znajdował się w tym samym adresie co obiekt innego typu.|
|**Okno**|Opcjonalny parametr **ciągu** .<br/><br/>Ścieżka folderu do katalogu głównego dla nagłówków i bibliotek.|
|**TargetArch**|Opcjonalny parametr **ciągu** .<br/><br/>Architektura docelowa.|
|**Kciukmode**|Opcjonalny parametr **ciągu** .<br/><br/>Generuj kod, który jest wykonywany dla mikroarchitektury przycisku przewijania. Dotyczy to tylko architektury ARM.<br/><br/>**Kciuk** , Generuj kod kciuka (Użyj `mthumb` ).<br/>**ARM** , Generuj kod ARM (Użyj `marm` ).<br/>**Wyłączone** , opcja nie dotyczy wybranej platformy.|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br/><br/>Katalog dziennika śledzenia.|
|**TreatWarningAsError**|Opcjonalny parametr **bool** .<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>W przypadku nowego projektu najlepiej jest używać go `/WX` we wszystkich kompilacjach; rozpoznanie wszystkich ostrzeżeń zapewni najmniejszą możliwą trudną do znalezienia wady kodu.|
|**UndefinePreprocessorDefinitions**|Opcjonalny parametr **String []** .<br/><br/>Określa co najmniej jedną definicję preprocesora.<br/><br/>Użyj polecenia `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Opcjonalny parametr **bool** .<br/><br/>Usuń wszystkie poprzednio zdefiniowane wartości preprocesora.<br/><br/>Użyj polecenia `-undef`.|
|**UseMultiToolTask**|Opcjonalny parametr **bool** .<br/><br/>Kompilacja wieloprocesorowa.|
|**UseShortEnums**|Opcjonalny parametr **bool** .<br/><br/>Typ wyliczenia używa tylko liczby bajtów wymaganej przez wejściowy zestaw możliwych wartości.|
|**Pełne**|Opcjonalny parametr **bool** .<br/><br/>Pokaż polecenia do uruchomienia i użyj pełnych danych wyjściowych.|
|**WarningLevel**|Opcjonalny parametr **ciągu** .<br/><br/>Wybierz, jak ścisłość kompilator ma mieć wpływ na błędy kodu. Inne flagi należy dodać bezpośrednio do **dodatkowych opcji** (SE `/w` , `/Weverything` ).<br/><br/>**TurnOffAllWarnings** , wyłącza wszystkie ostrzeżenia kompilatora (użycie `w` ).<br/>**Włącz wszystkie ostrzeżenia** , włącza wszystkie ostrzeżenia, w tym te wyłączone domyślnie (Użyj `Wall` ).|

## <a name="see-also"></a>Zobacz także

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
