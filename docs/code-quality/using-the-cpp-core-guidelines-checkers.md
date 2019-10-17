---
title: Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: fee4478f52cd107d2173919617aca8acd07234eb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445654"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++

C++ Podstawowe wytyczne są przenośnym zestawem wytycznych, zasad i najlepszych rozwiązań dotyczących kodowania C++ utworzonego przez C++ ekspertów i projektantów. Program Visual Studio obecnie obsługuje podzbiór tych reguł w ramach narzędzi do analizy kodu dla programu C++. Główne wskazówki sprawdzające podstawowe są instalowane domyślnie w programie Visual Studio 2017 i Visual Studio 2019 i są [dostępne jako pakiet NuGet dla programu Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projekt C++ podstawowych wytycznych

Podstawowe wytyczne są tworzone przez Bjarne'a Stroustrupa i C++ inne, ale w sposób C++ bezpieczny i efektywny. Wytyczne podkreślają bezpieczeństwo typu statycznego i bezpieczeństwo zasobów. Identyfikują one sposoby eliminacji lub minimalizowania najbardziej podatnych na błędy części języka, a także sugerują sposób prostszego i bardziej wydajnego wykonywania kodu. Te wytyczne są obsługiwane przez standardową C++ podstawę. Aby dowiedzieć się więcej, zobacz dokumentację, [ C++ podstawowe wytyczne](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)i dostęp do C++ plików projektu dokumentacji podstawowych wytycznych w serwisie [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz C++ podstawowe wskazówki dotyczące sprawdzania w analizie kodu
Możesz włączyć analizę kodu w projekcie, zaznaczając pole wyboru **Włącz analizę kodu podczas kompilacji** w sekcji **Analiza kodu** okna dialogowego **strony właściwości** dla projektu.

![Strona właściwości dla ustawień ogólnych analizy kodu](media/cppcorecheck_codeanalysis_general.png)

Podzbiór C++ podstawowych reguł sprawdzania jest zawarta w natywnym zalecanym przez firmę Microsoft zestawem reguł, który jest uruchamiany domyślnie po włączeniu analizy kodu. Aby włączyć dodatkowe podstawowe reguły sprawdzania, kliknij listę rozwijaną i wybierz zestawy reguł, które chcesz uwzględnić:

![Lista rozwijana C++ dla dodatkowych zestawów reguł sprawdzania podstawowego](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Przykłady
Oto przykład niektórych problemów, które mogą znaleźć C++ podstawowe reguły sprawdzania:

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

Ten przykład ilustruje kilka ostrzeżeń, które mogą znaleźć C++ podstawowe reguły sprawdzania:

- C26494 jest typem reguły. 5: zawsze Inicjuj obiekt.

- C26485 jest zakresem reguł. 3: brak zanikania tablicy do wskaźnika.

- C26481 jest zakresem reguł. 1: nie używaj arytmetyki wskaźnika. Zamiast nich należy używać słów kluczowych `span`.

Jeśli C++ podstawowe zestaw reguł analizy kodu są instalowane i włączane podczas kompilowania tego kodu, pierwsze dwa ostrzeżenia są wyjściowe, ale trzeci jest pomijany. Oto dane wyjściowe kompilacji z przykładowego kodu:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Podstawowe wskazówki ułatwiają pisanie lepszych i bezpieczniejszych kodów. Jeśli jednak istnieje wystąpienie, w którym nie należy stosować reguły lub profilu, można je łatwo pominąć bezpośrednio w kodzie. Można użyć atrybutu `gsl::suppress`, aby zachować C++ podstawowe sprawdzenie w wykrywaniu i raportowaniu naruszeń reguły w poniższym bloku kodu. Można oznaczyć poszczególne instrukcje, aby pominąć określone reguły. Można nawet pominąć profil całego ograniczenia, pisząc `[[gsl::suppress(bounds)]]` bez dołączania określonego numeru reguły.

## <a name="supported-rule-sets"></a>Obsługiwane zestawy reguł
W miarę dodawania nowych reguł do narzędzia C++ sprawdzania podstawowych wytycznych liczba ostrzeżeń, które są generowane dla istniejącego kodu, może się zwiększyć. Wstępnie zdefiniowanych zestawów reguł można użyć do filtrowania typów reguł do włączenia.
Tematy referencyjne dotyczące większości reguł znajdują się w sekcji [Visual Studio C++ Core Check Reference](code-analysis-for-cpp-corecheck.md).

W programie Visual Studio 2017 w wersji 15,3 obsługiwane są następujące zestawy reguł:
- **Reguły wskaźnika właściciela** wymuszają [operacje sprawdzania zarządzania zasobami powiązane ze współwłaścicielem @ no__t-2T C++ > od podstawowych wytycznych](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły const** wymuszają [kontrole związane z wartością stałą C++ z podstawowych wytycznych](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Reguły wskaźnika RAW** wymuszają [operacje sprawdzania zarządzania zasobami powiązane ze wskaźnikami nieprzetworzonymi z C++ podstawowych wskazówek](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły unikatowego wskaźnika** wymuszają [operacje sprawdzania zarządzania zasobami powiązane z typami z semantyką unikatowego C++ wskaźnika z podstawowych wytycznych](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły związane z ograniczeniami** wymuszają [profil ograniczenia C++ podstawowych wytycznych](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Reguły typu** wymuszają [Profil typu C++ podstawowych wytycznych](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Program Visual Studio 2017 w wersji 15,5**:

- **Reguły klas** Kilka reguł, które koncentrują się na właściwym użyciu specjalnych funkcji składowych i specyfikacji wirtualnych. Jest to podzbiór sprawdzań zalecany dla [klas i hierarchii klas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Reguły współbieżności** Pojedyncza reguła, która przechwytuje nieprawidłowo zadeklarowane obiekty Guard. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące współbieżności](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Reguły deklaracji** Kilka reguł z [wytycznych dotyczących interfejsów](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) , które koncentrują się na sposobie deklarowania zmiennych globalnych.
- **Reguły funkcji** Dwie kontrole, które pomagają w przyjęciu specyfikatora `noexcept`. Jest to część wytycznych dotyczących [projektowania i implementacji funkcji czyszczenia](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Reguły wspólnego wskaźnika** W ramach wymuszania wytycznych dotyczących [zarządzania zasobami](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) dodaliśmy kilka reguł specyficznych dla sposobu przekazywania współużytkowanych wskaźników do funkcji lub używanych lokalnie.
- **Reguły stylu** Jedna prosta, ale ważna kontrola, która zakazuje używania instrukcji [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Jest to pierwszy krok ulepszania stylu kodowania i używania wyrażeń i instrukcji w C++.

**Program Visual Studio 2017 w wersji 15,6**:

- **Reguły arytmetyczne** Reguły wykrywające [przepełnienie](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)arytmetyczne, [operacje podpisane bez znaku](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) i [manipulowanie bitowe](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Można wybrać ograniczenie ostrzeżeń tylko do jednej lub kilku grup. **Natywne minimalne** i **natywne zalecane** zestawy reguł C++ obejmują podstawowe reguły sprawdzania, a także inne szybkie testy. Aby wyświetlić dostępne zestawy reguł, Otwórz okno dialogowe właściwości projektu, wybierz pozycję **kod Analysis\General**, Otwórz listę rozwijaną w polu kombi **zestawy reguł** i wybierz **pozycję zaznacz wiele zestawów reguł**. Aby uzyskać więcej informacji o korzystaniu z zestawów reguł w programie Visual Studio, zobacz [używanie zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makra

Narzędzie C++ sprawdzania podstawowych wytycznych zawiera plik nagłówka, który definiuje makra, które ułatwiają pomijanie wszystkich kategorii ostrzeżeń w kodzie:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Te makra odpowiadają zestawom reguł i rozszerzają je na listę wartości ostrzeżeń rozdzielonych spacjami. Korzystając z odpowiednich konstrukcji dyrektywy pragma, można skonfigurować obowiązujący zestaw reguł, które są interesujące dla projektu lub sekcji kodu. W poniższym przykładzie Analiza kodu ostrzega tylko o brakujących modyfikatorach stałych:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atrybuty

Kompilator Microsoft Visual C++ Compiler ma ograniczoną obsługę atrybutu pomijania GSL. Może służyć do pomijania ostrzeżeń dotyczących wyrażeń i bloków instrukcji wewnątrz funkcji.

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

## <a name="suppress-analysis-by-using-command-line-options"></a>Pomiń analizę przy użyciu opcji wiersza polecenia

Zamiast #pragmas można użyć opcji wiersza polecenia na stronie właściwości pliku, aby pominąć ostrzeżenia dla projektu lub pojedynczego pliku. Na przykład aby wyłączyć ostrzeżenie 26400 dla pliku:

1. Kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań**

2. Wybierz **właściwości | C/C++| Wiersz polecenia**

3. W oknie **Opcje dodatkowe** Dodaj `/wd26400`.

Za pomocą opcji wiersza polecenia można tymczasowo wyłączyć wszystkie analizy kodu dla pliku, określając `/analyze-`. Spowoduje to wygenerowanie ostrzeżenia *D9025 przesłanianie "/ANALYZE" z "/ANALYZE-"* , co przypomina ponowne włączenie analizy kodu później.

## <a name="corecheck_per_file"></a>Włącz narzędzie C++ sprawdzania podstawowych wytycznych dla określonych plików projektu

Czasami warto skorzystać z ukierunkowanej analizy kodu i nadal używać środowiska IDE programu Visual Studio. Następujący przykładowy scenariusz może być używany w przypadku dużych projektów do zapisywania czasu kompilacji i ułatwiający filtrowanie wyników:

1. W powłoce poleceń Ustaw zmienne środowiskowe `esp.extension` i `esp.annotationbuildlevel`.
2. Aby odziedziczyć te zmienne, Otwórz program Visual Studio z poziomu powłoki poleceń.
3. Załaduj projekt i otwórz jego właściwości.
4. Włącz analizę kodu, wybierz odpowiednie zestawy reguł, ale nie włączaj rozszerzeń analizy kodu.
5. Przejdź do pliku, który chcesz analizować, za pomocą C++ narzędzia sprawdzania podstawowych wytycznych i otwórz jego właściwości.
6. Wybierz **Opcje liniiC++C/\Command** i Dodaj `/analyze:plugin EspXEngine.dll`
7. Wyłącz używanie prekompilowanego nagłówka (**nagłówki C/C++\Precompiled**). Jest to konieczne, ponieważ aparat rozszerzeń może próbować odczytać informacje wewnętrzne z prekompilowanego nagłówka (PCH); Jeśli PCH skompilowane z użyciem domyślnych opcji projektu, nie będzie zgodny.
8. Ponownie skompiluj projekt. Wspólne testy szybkie są uruchamiane na wszystkich plikach. Ponieważ narzędzie C++ sprawdzania podstawowych wytycznych nie jest domyślnie włączone, powinno być uruchamiane tylko na pliku, który jest skonfigurowany do korzystania z niego.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak używać narzędzia sprawdzania C++ podstawowych wytycznych poza programem Visual Studio

W przypadku zautomatyzowanych C++ kompilacji można użyć testów podstawowych wytycznych.

### <a name="msbuild"></a>MSBuild
Narzędzie sprawdzania kodu natywnego (wstępnie Fast) jest zintegrowane ze środowiskiem MSBuild przez pliki niestandardowych elementów docelowych. Możesz użyć właściwości projektu, aby je włączyć, i dodać C++ najważniejsze wskazówki (które są oparte na szybkim przełożeniu):

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Przed zaimportowaniem pliku Microsoft. cpp. targets należy dodać te właściwości. Można wybrać konkretne zestawy reguł lub utworzyć niestandardowy zestaw reguł lub użyć domyślnego zestawu reguł, który zawiera inne szybkie testy.

Program C++ Core Checker można uruchomić tylko dla określonych plików, korzystając z tego samego podejścia jak [opisane wcześniej](#corecheck_per_file), ale przy użyciu plików programu MSBuild. Zmienne środowiskowe można ustawić za pomocą elementu `BuildMacro`:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Jeśli nie chcesz modyfikować pliku projektu, możesz przekazać właściwości w wierszu polecenia:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projekty inne niż MSBuild

W przypadku korzystania z systemu kompilacji, który nie korzysta z programu MSBuild, nadal można uruchomić narzędzie sprawdzania, ale należy zapoznać się z niektórymi wewnętrznymi konfiguracją aparatu analizy kodu. Te wewnętrzne nie są gwarantowane w przyszłości.

Należy ustawić kilka zmiennych środowiskowych i użyć odpowiednich opcji wiersza polecenia dla kompilatora. Lepiej jest używać środowiska "natywnych narzędzi wiersza polecenia", dzięki czemu nie trzeba wyszukiwać określonych ścieżek dla kompilatora, zawierać katalogów itp.

1. **Zmienne środowiskowe**
   - `set esp.extensions=cppcorecheck.dll` to nakazuje aparatowi załadowanie C++ modułu podstawowych wytycznych.
   - `set esp.annotationbuildlevel=ignore` powoduje wyłączenie logiki, która przetwarza adnotacje SAL. Adnotacje nie wpływają na analizę kodu C++ w ramach sprawdzania podstawowych wytycznych, ale czas ich przetwarzania (czasami długi czas). To ustawienie jest opcjonalne, ale zdecydowanie zalecane.
   - `set caexcludepath=%include%` zdecydowanie zalecamy wyłączenie ostrzeżeń, które są uruchamiane w standardowych nagłówkach. W tym miejscu możesz dodać więcej ścieżek, na przykład ścieżkę do wspólnych nagłówków w projekcie.
2. **Opcje wiersza polecenia**
   - `/analyze` włącza analizę kodu (należy rozważyć także użycie/analyze: Only i/analyze: Quiet).
   - `/analyze:plugin EspXEngine.dll` ta opcja ładuje aparat rozszerzeń analizy kodu do przodu. Ten aparat, z kolei, ładuje C++ najważniejsze wskazówki.

## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki podstawowej pomocy technicznej
Podstawowa Biblioteka pomocy technicznej została zaprojektowana w celu ułatwienia przestrzegania podstawowych wytycznych. GSL zawiera definicje, które umożliwiają zamianę konstrukcji podatnych na błędy z bezpieczniejszymi alternatywami. Na przykład można zastąpić parę `T*, length` parametrów z typem `span<T>`. GSL jest dostępny w [http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl). Biblioteka jest open source, dzięki czemu można przeglądać źródła, wprowadzać komentarze lub współtworzyć. Projekt można znaleźć pod adresem [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Korzystanie z C++ podstawowych wskazówek dotyczących sprawdzania w projektach programu Visual Studio 2015

W przypadku korzystania z C++ programu Visual Studio 2015 zestawy reguł analizy kodu podstawowego nie są instalowane domyślnie. Należy wykonać kilka dodatkowych kroków, aby można było włączyć podstawowe C++ narzędzia do analizy kodu w programie Visual Studio 2015. Firma Microsoft zapewnia pomoc techniczną dla projektów programu Visual Studio 2015 przy użyciu pakietu NuGet. Pakiet ma nazwę Microsoft. CppCoreCheck i jest dostępny w [http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ten pakiet wymaga co najmniej programu Visual Studio 2015 z aktualizacją Update 1.

Pakiet instaluje również inny pakiet jako zależność, tylko w przypadku podstawowej biblioteki obsługi (GSL). GSL jest również dostępna w witrynie GitHub pod adresem [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

Ze względu na sposób ładowania reguł analizy kodu należy zainstalować pakiet NuGet Microsoft. CppCoreCheck w każdym C++ projekcie, który ma być sprawdzany w programie Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Aby dodać pakiet Microsoft. CppCoreCheck do projektu w programie Visual Studio 2015

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, do którego chcesz dodać pakiet. Wybierz pozycję **Zarządzaj pakietami NuGet** , aby otworzyć **Menedżera pakietów NuGet**.

2. W oknie **Menedżer pakietów NuGet** Wyszukaj ciąg Microsoft. CppCoreCheck.

    ![Okno Menedżera pakietów NuGet zawiera pakiet CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Wybierz pakiet Microsoft. CppCoreCheck, a następnie wybierz przycisk **Instaluj** , aby dodać reguły do projektu.

   Pakiet NuGet dodaje do projektu dodatkowy plik MSBuild *. targets* , który jest wywoływany po włączeniu analizy kodu dla projektu. Ten plik *targets* dodaje C++ podstawowe reguły sprawdzania jako dodatkowe rozszerzenie narzędzia do analizy kodu programu Visual Studio. Po zainstalowaniu pakietu można użyć okna dialogowego strony właściwości, aby włączyć lub wyłączyć reguły wydane i eksperymentalne.

## <a name="see-also"></a>Zobacz też

- [Podstawowe informacje C++ o sprawdzaniu programu Visual Studio](code-analysis-for-cpp-corecheck.md)
