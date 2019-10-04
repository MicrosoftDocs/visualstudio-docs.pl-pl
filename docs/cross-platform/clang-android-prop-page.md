---
title: Właściwości projektu Clang (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 7c64ccedaeb8c13e353daaba0aeec0a388885bdf
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950652"
---
# <a name="clang-project-properties-android-c"></a>Właściwości projektu Clang (Android C++)

Właściwość | Opis | Decyzji
--- | ---| ---
Dodatkowe katalogi dołączane | Określa co najmniej jeden katalog do dodania do ścieżki dołączania; Oddzielaj średnikami, jeśli więcej niż jeden. (-I [ścieżka]).
Format informacji o debugowaniu | Określa typ informacji o debugowaniu generowanych przez kompilator. | **Brak** — nie tworzy informacji o debugowaniu, dzięki czemu kompilacja może być szybsza.<br>**Pełne informacje o debugowaniu (DWARF2)** — generują informacje debugowania DWARF2.<br>**Informacje o numerze wiersza** — Generuj tylko informacje o numerze wiersza.<br>
Nazwa pliku obiektu | Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu; może to być nazwa pliku lub katalogu. (/Fo [nazwa]).
Poziom ostrzeżeń | Wybierz, jak ścisłość kompilator ma mieć wpływ na błędy kodu.  Inne flagi należy dodać bezpośrednio do dodatkowych opcji. (/w,/Weverything). | Wyłącz **wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br>**Włącz wszystkie ostrzeżenia** — włącza wszystkie ostrzeżenia, w tym te, które są domyślnie wyłączone.<br>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. W przypadku nowego projektu najlepiej jest używać/WX we wszystkich kompilacjach. rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą możliwą trudną do znalezienia wady kodu.
Włącz tryb pełny | Pokaż polecenia do uruchomienia i użyj pełnych danych wyjściowych.
Optymalizacja | Określa poziom optymalizacji aplikacji. | Optymalizacja **niestandardowa** .<br>**Wyłączone** — wyłączenie optymalizacji.<br>**Minimalizuj rozmiar** — Optymalizuj pod kątem rozmiaru.<br>**Maksymalizuj szybkość** — Optymalizuj szybkość.<br>**Pełna optymalizacja** — kosztowna Optymalizacja.<br>
Jednostrictne aliasowanie | Przyjęto założenie rygorystycznych reguł aliasów.  Obiekt jednego typu nigdy nie zostanie przyjęty, aby znajdował się w tym samym adresie co obiekt innego typu.
Pomiń wskaźnik ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Włącz C++ wyjątki | Określa model obsługi wyjątków, który ma być używany przez kompilator. | **Nie** -Wyłącz obsługę wyjątków.<br>**Tak** — Włącz obsługę wyjątków.<br>**Tabele unwinds** — generuje wszystkie potrzebne dane statyczne, ale nie ma wpływu na wygenerowany kod.<br>
Włącz łączenie na poziomie funkcji | Umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT). Wymagane do edycji i kontynuowania pracy.     (ffunction — sekcje).
Włącz łączenie na poziomie danych | Umożliwia optymalizacjom konsolidatora usuwanie nieużywanych danych przez emitowanie każdego elementu danych w osobnej sekcji.
Włącz zaawansowane SIMD (neon) | Włącza generowanie kodu dla sprzętu zmiennoprzecinkowego NEONu. Dotyczy to tylko architektury ARM.
ABI zmiennoprzecinkowe | Opcja wyboru umożliwiająca wybranie ABI zmiennoprzecinkowego. | **Soft** -"Soft" powoduje, że kompilator generuje dane wyjściowe zawierające wywołania biblioteki dla operacji zmiennoprzecinkowych.<br>**SoftFP** -"SoftFP" umożliwia generowanie kodu przy użyciu instrukcji zmiennoprzecinkowych sprzętu, ale nadal używa konwencji wywoływania miękkie-zmiennoprzecinkowych.<br>**Twarda** "twarda" umożliwia generowanie instrukcji zmiennoprzecinkowych i używa konwencji wywoływania specyficznych dla FPU.<br>
Sprawdzanie zabezpieczeń | Kontrola zabezpieczeń pomaga wykrywać bufory stosu w trybie failover, typowy atak na zabezpieczenia programu. (fstack-funkcja ochrony). | **Wyłącz sprawdzanie zabezpieczeń** — Wyłącz sprawdzanie zabezpieczeń.<br>**Włącz sprawdzanie zabezpieczeń** — Włącz sprawdzanie zabezpieczeń. (fstack-ochrona)<br>
Umieść kod niezależny | Generuj kod niezależnej pozycji (PIC) do użycia w bibliotece udostępnionej.
Użyj krótkich wyliczeń | Typ wyliczenia używa tylko liczby bajtów wymaganej przez wejściowy zestaw możliwych wartości.
Włącz informacje o typie w czasie wykonywania | Dodaje kod do sprawdzania C++ typów obiektów w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, FNO-RTTI)
Standard języka C | Określa standard języka C. | **Domyślne**<br>Standard języka **C89** -c89.<br>Standard języka **C99** -C99.<br>Standard języka **C11** -C11.<br>Standard języka **C99 (DIALEKT GNU)** — C99 (dialekt GNU).<br>Standard języka **C11 (DIALEKT GNU)** — C11 (dialekt GNU).<br>
C++Standard języka | Określa standard C++ języka. | **Domyślne**<br>Standard języka **C++ 03** -c++ 03.<br>Standard języka **C++ 11** — c++ 11.<br>Standard języka **C++ 14** -c++ 14.<br>**C++ 03 (DIALEKT GNU)** — Standard języka c++ 03 (dialekt GNU).<br>**C++ 11 (DIALEKT GNU)** — Standard języka c++ 11 (dialekt GNU).<br>**C++ 14 (DIALEKT GNU)** — Standard języka c++ 14 (dialekt GNU).<br>
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń Definicje preprocesora | Określa co najmniej jedną definicję preprocesora.  (-U [makro])
Usuń wszystkie Definicje preprocesora | Usuń wszystkie poprzednio zdefiniowane wartości preprocesora.  (-undef)
Pokaż zawiera | Generuje listę plików dołączanych z danymi wyjściowymi kompilatora.  (-H)
Prekompilowany nagłówek | Utwórz/Użyj prekompilowanego nagłówka: umożliwia utworzenie lub użycie prekompilowanego nagłówka podczas kompilowania. | **Użyj** — Użyj prekompilowanego nagłówka.<br>**Nie używa prekompilowanych nagłówków** — nie używa prekompilowanego nagłówka.<br>
Prekompilowany plik nagłówkowy | Określa nazwę pliku nagłówkowego, który ma być używany dla prekompilowanego pliku nagłówkowego. Ten plik zostanie również dodany do "wymuszonych plików dołączanych" podczas kompilacji
Katalog prekompilowanego wyjściowego pliku nagłówkowego | Określa katalog dla wygenerowanego prekompilowanego nagłówka. Ten katalog zostanie również dodany do "dodatkowych katalogów dołączanych" podczas kompilacji
Kompiluj prekompilowany nagłówek jako | Wybierz opcję języka kompilowania dla prekompilowanego pliku nagłówkowego (-x c-header,-x c++-header). | **Kompiluj jako kod c** Kompiluj jako kod c.<br>**Kompiluj jako C++**  kod Kompiluj jako C++ kod.<br>
Kompiluj jako | Wybierz opcję Język kompilacji dla plików. c i. cpp.  Element "default" zostanie wykryty w oparciu o rozszerzenie. c lub. cpp. (-x c, -x c++) | **Domyślne** — domyślnie.<br>**Kompiluj jako kod c** Kompiluj jako kod c.<br>**Kompiluj jako C++**  kod Kompiluj jako C++ kod.<br>
Wymuszone pliki dołączane | co najmniej jeden wymuszony plik dyrektywy include.     (-include [nazwa])
Kompilacja wieloprocesorowa | Kompilacja wieloprocesorowa.
Opcje dodatkowe | Opcje dodatkowe.
