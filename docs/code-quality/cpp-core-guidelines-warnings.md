---
title: Ostrzeżenia dotyczące podstawowych wytycznych dotyczących języka C++
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 556821ff934d8276622ffb12ddbf4589ac404ab8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661389"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++

Podstawowych wytycznych dotyczących języka C++ są przenośne zbiór wytycznych, reguł i najlepsze rozwiązania dotyczące programowania w języku C++, utworzone przez ekspertów z C++ i projektantów. Program Visual Studio obsługuje obecnie podzbiór tych reguł w ramach jego narzędzi analizy kodu dla języka C++. Podstawowe wytyczne są instalowane domyślnie w programie Visual Studio 2017 i Visual Studio 2019 r oraz są [dostępne jako pakiet NuGet dla programu Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>C++ podstawowych wytycznych dotyczących projektu

Utworzone przez Bjarne'a Stroustrupa i innym osobom, podstawowych wytycznych dotyczących języka C++ to przewodnik do wykorzystania nowoczesnym języku C++, bezpiecznie i wydajnie. Wytyczne podkreślić bezpieczeństwa typu statycznego i bezpieczeństwa zasobów. Identyfikowanie sposoby wyeliminowania lub zminimalizować najbardziej podatne na błędy części języka i sugeruje jak sprawić, że kod jest prostszy i wydajniej w niezawodny sposób. Te wytyczne są obsługiwane przez Standard C++ Foundation. Aby dowiedzieć się więcej, zapoznaj się z dokumentacją, [podstawowych wytycznych dotyczących języka C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), a dostęp do plików projektu dokumentacji podstawowych wytycznych dotyczących języka C++ na [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz wskazówki podstawowe sprawdzanie języka C++ w analizie kodu

Można włączyć analizę kodu projektu, wybierając **Włącz analizę kodu podczas kompilacji** pola wyboru w **analizy kodu** części **stron właściwości** okno dialogowe Projekt.

![Strony właściwości dla ustawień ogólnych analizy kodu](../code-quality/media/cppcorecheck_codeanalysis_general.png)

Podstawowe sprawdzanie języka C++ reguły są rozszerzenia do zestawów reguł domyślne, które są uruchamiane po włączeniu analizy kodu. Ponieważ zasady podstawowe sprawdzanie języka C++, są w fazie projektowania, niektóre reguły dobrze się, a niektóre mogą nie być gotowe do użycia na cały kod, ale może być zawierającego wiele użytecznych informacji. Reguły są podzielone na dwie grupy: zwolniono i eksperymentalne. Możesz wybrać, czy do uruchamiania reguły wydana lub eksperymentalnych we właściwościach projektu.

![Strony właściwości dla ustawień rozszerzenia analizy kodu](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

Aby włączyć lub wyłączyć zestawy reguł podstawowe sprawdzanie języka C++, otwórz **stron właściwości** okno dialogowe dla Twojego projektu. W obszarze **właściwości konfiguracji**, rozwiń węzeł **analizy kodu**, **rozszerzenia**. W menu rozwijanym obok kontrolować **Włącz podstawowe sprawdzanie języka C++ (wydania)** lub **Włącz podstawowe sprawdzanie języka C++ (funkcja eksperymentalna)**, wybierz **tak** lub **nie**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="examples"></a>Przykłady

Oto przykład niektórych problemów, które można znaleźć reguły podstawowe sprawdzanie języka C++:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

W tym przykładzie pokazano kilka ostrzeżeń, które można znaleźć reguły podstawowe sprawdzanie języka C++:

- C26494 jest regułą Type.5: Zawsze Inicjuj obiekt.

- C26485 jest regułą Bounds.3: Nie zanikania tablicy do wskaźnika.

- C26481 jest regułą Bounds.1: Nie używaj arytmetyki wskaźnika. Zamiast nich należy używać słów kluczowych `span`.

Jeśli zestawów reguł podstawowe sprawdzanie języka C++ analizy kodu są zainstalowane i włączone, skompilować ten kod, pierwsze dwa ostrzeżenia są dane wyjściowe, ale trzecie jest pomijane. Oto dane wyjściowe kompilacji z przykładowego kodu:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Podstawowych wytycznych dotyczących języka C++, istnieją ułatwia pisanie kodu lepsze i bezpieczniejsze. Jednak w przypadku wystąpienia, gdzie nie należy zastosować regułę lub profil jest łatwy do pomijania go bezpośrednio w kodzie. Możesz użyć `gsl::suppress` atrybutu, aby zapobiec podstawowe sprawdzanie języka C++ wykrywania i raportowania wszelkie naruszenia reguły w następującym fragmencie kodu. Możesz oznaczyć pojedyncze instrukcje, aby pominąć określone zasady. Można nawet pominąć cały profil granic, pisząc `[[gsl::suppress(bounds)]]` bez uwzględniania numer określonej reguły.

## <a name="supported-rule-sets"></a>Obsługiwane zestawy reguł

Po dodaniu nowych zasad do wytycznych podstawowe sprawdzanie języka C++, może wzrosnąć liczba ostrzeżeń, które są tworzone dla wcześniej napisanego kodu. Zestawy wstępnie zdefiniowanych reguł można użyć do filtrowania, jakie rodzaje zasad, aby włączyć. Począwszy od programu Visual Studio 2017 w wersji 15.3 zestawów reguł obsługiwane są:

  - **Właściciel — reguły dotyczące wskaźnika** wymusić [zarządzania zasobami sprawdza związane z właścicielem\<T > podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Reguły dotyczące zmiennych** wymusić [operacje sprawdzania powiązane z podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Reguły dotyczące wskaźnika surowego** wymusić [sprawdza, zarządzania zasobami powiązane z surowe wskaźniki podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Unikatowe reguły dotyczące wskaźnika** wymusić [zarządzania zasobami sprawdza powiązane z typami z semantyką unikatowego wskaźnika podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Reguły dotyczące granic** wymusić [granic profilu podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Reguły typu** wymusić [typu profilu podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

Można ograniczyć ostrzeżeń do tylko jednej lub kilku grup. **Native Minimum** i **natywny zalecany** reguły zestawy reguł podstawowe sprawdzanie języka C++, oprócz innych PREfast kontroli. Aby wyświetlić dostępnych zestawów reguł, Otwórz okno dialogowe właściwości projektu, wybierz **Analysis\General kodu**, Otwórz na liście rozwijanej **zestawów reguł** pola kombi i pobrania **Wybierz wiele zestawów reguł** . Aby uzyskać więcej informacji na temat Korzystanie z zestawów reguł w programie Visual Studio, zobacz [przy użyciu zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makra

Wytyczne dotyczące podstawowe sprawdzanie języka C++ jest dostarczany z pliku nagłówka, który definiuje makra, które ułatwiają Pomiń całych kategorii ostrzeżeń w kodzie:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Te makra odpowiadają zestawów reguł i rozszerzyć do rozdzielonej spacjami listy numerów ostrzeżeń. Za pomocą konstrukcji odpowiednie pragma można skonfigurować efektywne zestaw reguł, który jest interesujące dla projektu lub sekcji kodu. W poniższym przykładzie analizę kodu tylko wyświetli ostrzeżenie o brakujące Modyfikatory stałe:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atrybuty

Kompilator Microsoft Visual C++ ma ograniczoną obsługę GSL Pomiń atrybut. Może służyć do Pomijaj ostrzeżenia w przypadku wyrażeń i instrukcji bloku wewnątrz funkcji.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Pomijanie analizy przy użyciu opcji wiersza polecenia

Zamiast #pragmas umożliwia opcje wiersza polecenia na stronie właściwości pliku pomijanie ostrzeżeń dla projektu lub pojedynczy plik. Na przykład, aby wyłączyć ostrzeżenia 26400 dla pliku:

1. Kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**

2. Wybierz **właściwości | C / C ++ | Wiersz polecenia**

3. W **dodatkowe opcje** oknie Dodaj `/wd26400`.

Można użyć opcji wiersza polecenia, aby tymczasowo wyłączyć wszystkie analizy kodu dla pliku, określając `/analyze-`. Generuje to ostrzeżenie *zastępowanie D9025 "/ analyze" z "/ analyze-"*, która wyświetli Ci przypomnienie po można ponownie włączyć później analizy kodu.

## <a name="corecheck_per_file"></a> Włączanie podstawowe sprawdzanie języka C++ wytyczne dotyczące plików w określonym projekcie

Czasami może być przydatne do analizy kodu czy skupia się i nadal korzystaj środowiska IDE programu Visual Studio. Poniżej przedstawiono przykładowy scenariusz, który może służyć do dużych projektów, aby zapisać czas kompilacji i ułatwić filtrowania wyników.

1. W powłoce poleceń ustaw `esp.extension` i `esp.annotationbuildlevel` zmiennych środowiskowych.
2. Otwórz program Visual Studio z powłoki poleceń w celu odziedziczenia tych zmiennych.
3. Ładowanie projektu i otwórz jej właściwości.
4. Włącz analizę kodu, wybierz odpowiednią reguł, ale nie należy włączać rozszerzenia analizy kodu.
5. Przejdź do pliku, który chcesz analizować za pomocą wytycznych podstawowe sprawdzanie języka C++ i otwórz jej właściwości.
6. Wybierz **C / C ++ \Command opcje linii** i Dodaj `/analyze:plugin EspXEngine.dll`
7. Wyłącz używaniem prekompilowanego nagłówka (**C / C ++ \Precompiled nagłówki**). Jest to konieczne, ponieważ aparat rozszerzenia może próbować odczytywać wewnętrznych informacji prekompilowanego pliku nagłówkowego, a jeśli one został skompilowany przy użyciu domyślnej opcji projektu, nie będzie zgodny.
8. Skompiluj ponownie projekt. Typowe kontrole PREFast należy uruchomić we wszystkich plikach. Wytyczne dotyczące podstawowe sprawdzanie języka C++ nie jest domyślnie włączona, dlatego go powinien działać tylko na pliku, który jest skonfigurowany do używania go.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak używać podstawowe sprawdzanie języka C++ wytycznych poza programem Visual Studio
Sprawdzanie w podstawowych wytycznych dotyczących języka C++ można użyć w kompilacjach zautomatyzowanych.

### <a name="msbuild"></a>MSBuild

Narzędzie do sprawdzania analizy kodu natywnego (PREfast) jest zintegrowana środowiska MSBuild przez pliki niestandardowych elementów docelowych. Można użyć właściwości projektu, aby ją włączyć, a następnie dodaj podstawowe sprawdzanie wytyczne dotyczące języka C++, (które opiera się na PREfast):

```xml
<PropertyGroup>
  <EnableCppCoreCheck>true</EnableCppCoreCheck>
  <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
  <RunCodeAnalysis>true</RunCodeAnalysis>
</PropertyGroup>
```

Upewnij się, że możesz dodać te właściwości, przed zaimportowaniem pliku Microsoft.Cpp.targets. Można wybrać zestawów reguł określone lub Tworzenie niestandardowego zestawu reguł lub użycie domyślnego zestawu reguł, zawierający inne kontrole PREfast.

Podstawowe sprawdzanie języka C++ można uruchomić tylko na określonych plików, przy użyciu tej samej metody co [opisanej wcześniej](#corecheck_per_file), ale przy użyciu plików programu MSBuild. Zmienne środowiskowe można ustawić za pomocą `BuildMacro` elementu:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Jeśli nie chcesz zmodyfikować plik projektu, można przekazać właściwości w wierszu polecenia:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projekty inne niż MSBuild
Jeśli używasz systemu kompilacji, który nie jest zależny od programu MSBuild, nadal można uruchomić narzędzie sprawdzania, ale należy zapoznać się z niektóre funkcje wewnętrzne Konfiguracja aparatu analizy kodu, (która jest nie musi być obsługiwane w przyszłości).

Należy ustawić kilka zmiennych środowiskowych i użyć właściwych opcji wiersza polecenia dla kompilatora. Zaleca się pracować w ramach środowiska "natywnych wiersz polecenia narzędzi", dzięki czemu nie trzeba wyszukiwania dla określonych ścieżek dla kompilatora, obejmują katalogi itp.

1. **Zmienne środowiskowe**
   - `set esp.extensions=cppcorecheck.dll` Oznacza to, aparat, który można załadować modułu podstawowych wytycznych dotyczących języka C++.
   - `set esp.annotationbuildlevel=ignore` Powoduje to wyłączenie logiki, która przetwarza adnotacji SAL. Adnotacji nie mają wpływu na analizę kodu w wytycznych podstawowe sprawdzanie języka C++, ale trwa jego przetwarzanie czasu (czasami dużo czasu). To ustawienie jest opcjonalne, lecz zdecydowanie zalecane.
   - `set caexcludepath=%include%` Zdecydowanie zalecamy, aby wyłączyć ostrzeżenia, które są uruchamiane na standardowych nagłówków. Możesz dodać więcej ścieżek, na przykład ścieżki do typowych nagłówków w projekcie.
2. **Opcje wiersza polecenia**
   - `/analyze`  Włącza analizę kodu (należy wziąć pod uwagę, również przy użyciu / analyze: tylko i / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Ta opcja ładuje aparatu rozszerzenia analizy kodu do PREfast. Ten aparat ładuje z kolei wytycznych podstawowe sprawdzanie języka C++.

## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki obsługi wskazówek dotyczących

Biblioteka obsługi wskazówek dotyczących zaprojektowano w celu postępuj zgodnie z podstawowych wytycznych dotyczących. GSL zawiera definicje, które umożliwiają Zamień podatne konstrukcje bezpieczniejszych alternatyw. Na przykład, możesz zastąpić `T*, length` pary parametrów za pomocą `span<T>` typu. GSL znajduje się w temacie [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Biblioteka jest typu open source, dzięki czemu można wyświetlić źródła, dodawać komentarze lub współtworzyć. Projekt, można znaleźć w folderze [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Użyj wytycznych podstawowe sprawdzanie języka C++ w projektach programu Visual Studio 2015

Jeśli używasz programu Visual Studio 2015, zestawów reguł analizy kodu podstawowe sprawdzanie języka C++ nie są zainstalowane domyślnie. Aby można było włączyć narzędzi analizy kodu podstawowe sprawdzanie języka C++ w programie Visual Studio 2015, należy wykonać kilka dodatkowych kroków. Firma Microsoft zapewnia obsługę dla projektów programu Visual Studio 2015, przy użyciu pakietu Nuget. Pakiet o nazwie Microsoft.CppCoreCheck i jest on dostępny w [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ten pakiet wymaga, że masz co najmniej zainstalowanego programu Visual Studio 2015 z aktualizacją Update 1.

Pakiet instaluje też inny pakiet jako zależność, tylko nagłówek wskazówek dotyczących pomocy technicznej biblioteki (GSL). GSL jest również dostępna w witrynie GitHub pod [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Ze względu na sposób, w jaki są ładowane reguł analizy kodu należy zainstalować pakiet Microsoft.CppCoreCheck NuGet do każdego projektu C++, który chcesz sprawdzić w programie Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Aby dodać pakiet Microsoft.CppCoreCheck do projektu w programie Visual Studio 2015

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, które chcesz dodać pakiet do. Wybierz **Zarządzaj pakietami NuGet** otworzyć **Menedżera pakietów NuGet**.

2. W **Menedżera pakietów NuGet** okna, wyszukaj Microsoft.CppCoreCheck.

    ![Pokazuje okno Menedżera pakietów Nuget, pakietów CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Wybierz pakiet Microsoft.CppCoreCheck, a następnie wybierz **zainstalować** przycisk, aby dodać reguły do projektu.

   Pakiet NuGet dodaje dodatkowe pliki .targets MSBuild do projektu, która jest wywoływana po włączeniu analizy kodu w projekcie. Ten plik .targets dodaje zasady podstawowe sprawdzanie języka C++ jako dodatkowe rozszerzenia narzędzie do analizy kodu programu Visual Studio. Po zainstalowaniu pakietu można użyć okna dialogowego strony właściwości do włączania lub wyłączania reguły zwolniono i eksperymentalne.
