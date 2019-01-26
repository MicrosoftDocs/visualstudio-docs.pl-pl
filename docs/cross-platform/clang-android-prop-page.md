---
title: Clang właściwości projektu (Android C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 055ec15deed2e5071c50d9903779d00030e07b02
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956236"
---
# <a name="clang-project-properties-android-c"></a>Właściwości projektu clang (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Dodatkowe katalogi dyrektywy Include | Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna. (-I[path]).
Format informacji o debugowaniu | Określa typ informacji o debugowaniu generowanych przez kompilator. | **Brak** — tworzy żadnych informacji debugowania, więc kompilacja może przebiegać szybciej.<br>**Pełne informacje debugowania (DWARF2)** — Generowanie debugowania dwarf2.<br>**Informacje o numerze wiersza** — tylko informacje o numerze wiersza wygenerować.<br>
Nazwa pliku obiektu | Określa nazwę do zastąpienia domyślnej nazwy pliku obiektu; może być nazwą pliku lub katalogu. (/ FO[nazwa]).
Poziom ostrzeżeń | Wybierz jak ścisły kompilator o błędów kodu.  Inne flagi należy dodać bezpośrednio do dodatkowych opcji. (/ w, / weverything). | **Włącz Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br>**EnableAllWarnings** -włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone.<br>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu ona najlepszym rozwiązaniem może być użycie elementu /WX we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą liczbą wad możliwe kodu twardych do znalezienia.
Włącz tryb informacji pełnej | Pokaż polecenia umożliwiające uruchomienie i użycie pełnych danych wyjściowych.
Optymalizacja | Określa poziom optymalizacji aplikacji. | **Niestandardowe** — niestandardowa Optymalizacja.<br>**Wyłączone** -Wyłącz optymalizację.<br>**Minimalizuj rozmiar** — Optymalizuj pod kątem rozmiaru.<br>**Maksymalizuj szybkość** — Optymalizuj pod kątem szybkości.<br>**Pełna optymalizacja** — kosztowne optymalizacje.<br>
Aliasowanie z ograniczeniami | Przyjęto założenie, najbardziej rygorystyczne reguły aliasowania.  Obiekt danego typu zostanie nigdy nie być zakłada się, że znajdują się na tym samym adresem co obiekt innego typu.
Pominięcie wskaźnika ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Włącz wyjątki języka C++ | Określa model obsługi wyjątków, aby używane przez kompilator. | **Nie** -Wyłącz obsługę wyjątków.<br>**Tak** -Włącz obsługę wyjątków.<br>**Odwiń tabele** — generuje wszelkie wymagane dane statyczne, ale nie ma wpływu na wygenerowany kod.<br>
Włącz łączenie na poziomie funkcji | Umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat). Wymagane do edycji i kontynuować pracę.     (ffunction Section).
Włącz łączenie na poziomie danych | Umożliwia optymalizacjom konsolidatora usuwanie nieużywanych danych przez emitowanie każdego elementu danych w osobnej sekcji.
Włącz zaawansowane instrukcje SIMD(Neon) | Umożliwia generowanie kodu dla sprzętu zmiennoprzecinkowego NEON. Dotyczy tylko architektury arm.
Zmiennoprzecinkowy interfejs ABI | Opcja umożliwiająca wybranie zmiennoprzecinkowego interfejsu ABI. | **Elastyczne** — "soft" umożliwia kompilatorowi Generowanie danych wyjściowych zawierających wywołania bibliotek dotyczące operacji zmiennoprzecinkowych.<br>**SoftFP** — "SoftFP" umożliwia generowanie kodu przy użyciu instrukcji zmiennoprzecinkowych sprzętu, ale nadal używa konwencji wywoływania zmiennoprzecinkowych.<br>**Twarde** — "Silne" umożliwia generowanie instrukcji zmiennoprzecinkowych i używa konwencji wywoływania specyficznych dla operacji FPU.<br>
Sprawdzanie zabezpieczeń | Kontrola zabezpieczeń pomaga wykryć stosu przepełnień buforu, typowy atak na zabezpieczenia programu. (fstack-protector). | **Wyłącz sprawdzanie zabezpieczeń** -Wyłącz sprawdzanie zabezpieczeń.<br>**Włącz sprawdzanie zabezpieczeń** -Włącz sprawdzanie zabezpieczeń. (fstack-protector)<br>
Kod niezależny od położenia | Generowanie niezależnie od kodu położenia (PIC) do użycia w bibliotece udostępnionej.
Użyj krótkich wyliczeń | Typ wyliczenia używa tylko liczby bajtów wymaganej przez wejściowy zestaw możliwych wartości.
Włącz informacje typu Run-Time | Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, fno-rtti)
Standard języka C | Określa standard języka C. | **Default**<br>**C89** — Standard języka C89.<br>**C99** — Standard języka C99.<br>**C11** — Standard języka C11.<br>**C99 (dialekt GNU)** — Standard języka programu C99 (dialekt GNU).<br>**C11 (dialekt GNU)** — Standard języka programu C11 (dialekt GNU).<br>
Standard języka C++ | Określa standard języka C++. | **Default**<br>**C ++ 03** — Standard C ++ 03 języka.<br>**C ++ 11** — Standard C ++ 11 język.<br>**C ++ 14** — Standard C ++ 14 języka.<br>**C ++ 03 (dialekt GNU)** — C ++ 03 (dialekt GNU) języka Standard.<br>**C ++ 11 (dialekt GNU)** — C ++ 11 (dialekt GNU) języka Standard.<br>**C ++ 14 (dialekt GNU)** — C ++ 14 (dialekt GNU) języka Standard.<br>
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń definicje preprocesora | Określa, że jedno anulowanie definicji preprocesora jeden lub więcej.  (-U [macro])
Usuń wszystkie definicje preprocesora | Usuń definicje wszystkich zdefiniowanych wcześniej wartości preprocesora.  (-undef)
Pokaż zawierania | Generuje listę załączonych plików z danych wyjściowych kompilatora.  (-H)
Prekompilowany plik nagłówkowy | Utworzenie/użycie Prekompilowanego nagłówka: umożliwia utworzenie lub użycie prekompilowanego nagłówka podczas kompilacji. | **Użyj** — Użyj Prekompilowanego nagłówka.<br>**Nie używa prekompilowanych nagłówków** — nie używa Prekompilowanego nagłówka.<br>
Prekompilowany plik nagłówka | Określa nazwę pliku do użycia dla prekompilowanego pliku nagłówkowego. Ten plik zostanie też dodany do "Wymuszone pliki dyrektywy Include" podczas kompilacji
Katalog pliku danych wyjściowych prekompilowanego nagłówka | Określa katalog wygenerowanego prekompilowanego pliku nagłówkowego. Ten katalog zostanie też dodany do elementu "Dodatkowe katalogi dołączenia" podczas kompilacji
Kompiluj prekompilowany nagłówek jako | Wybierz język kompilacji dla prekompilowanego pliku nagłówkowego (- x c-header, - x c ++ - nagłówek). | **Kompiluj jako kod C** — Kompiluj jako kod C.<br>**Kompiluj jako kod C++** — Kompiluj jako kod C++.<br>
Kompiluj jako | Wybierz opcję języka kompilowania dla plików .c i .cpp.  "Default" wykryje na podstawie rozszerzenia c lub CPP rozszerzenie. (-x c, -x c++) | **Domyślne** — domyślne.<br>**Kompiluj jako kod C** — Kompiluj jako kod C.<br>**Kompiluj jako kod C++** — Kompiluj jako kod C++.<br>
Wymuszone pliki dołączane | co najmniej jeden wymuszony plik dyrektywy dołączyć pliki.     (-include [nazwa])
Kompilacja wieloprocesorowa | Kompilacja wieloprocesorowa.
Dodatkowe opcje | Dodatkowe opcje.
