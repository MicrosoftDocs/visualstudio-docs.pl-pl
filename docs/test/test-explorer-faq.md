---
title: Eksplorator testów — często zadawane pytania
ms.date: 08/14/2019
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: jillfra
ms.openlocfilehash: cec8ea3ea091ab1ea65bcad2bd4cca139fd74042
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846807"
---
# <a name="visual-studio-test-explorer-faq"></a>— Często zadawane pytania dotyczące Eksploratora testów programu Visual Studio
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Gdzie jest grupa według cech w programie Visual Studio 2019?
To grupowanie cech zostało przeniesione do kolumny. Dzięki wielopoziomowej i konfigurowalnej hierarchii w programie Visual Studio 2019 w wersji 16.2 pomyśleliśmy, że uwzględnienie cech jako grupowania stworzyło niepotrzebną złożoność wizualną. Zdecydowanie słuchamy opinii na temat tego projektu! https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Na razie możesz kliknąć prawym przyciskiem myszy kolumnę w Eksploratorze testów i wybrać kolumny. Sprawdź kolumnę Cecha, która pojawi się w Eksploratorze testów. Teraz możesz filtrować tę kolumnę według interesujących Cię cech.

![Wyświetlanie kolumny](media/vs-2019/trait-column.png)
![Cecha Filtruj kolumnę cecha](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Dynamiczne odnajdowanie testów

**Eksplorator testów nie odnajduje moich testów, które są dynamicznie zdefiniowane. (Na przykład teorie, niestandardowe adaptery, niestandardowe cechy, #ifdefs itp.) Jak mogę odkryć te testy?**

::: moniker range=">=vs-2019"
Tworzenie projektu do uruchamiania odnajdowania opartego na zestawie.
::: moniker-end
::: moniker range="vs-2017"
Skompiluj swój projekt i upewnij się, że odnajdowanie oparte na zestawie jest włączone w **teście** **opcji** > **narzędzi** > .
::: moniker-end
[Odnajdowanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) jest odnajdywania testów opartych na źródle. Nie można wykryć testów, które używają teorii, niestandardowych kart, niestandardowych cech, `#ifdef` instrukcji i innych, ponieważ są one zdefiniowane w czasie wykonywania. Kompilacja jest wymagana dla tych testów, które mają być dokładnie znalezione. W programie Visual Studio 2017 w wersji 15.6 i nowszych odnajdowanie oparte na zestawie (odnajdywanie tradycyjne) jest uruchamiane tylko po kompilacjach. To ustawienie oznacza, że odnajdowanie testów w czasie rzeczywistym wynajduje tyle testów, ile może podczas edycji, a odnajdowanie oparte na zestawie umożliwia dynamicznie zdefiniowane testy po kompilacji. Odnajdowanie testów w czasie rzeczywistym poprawia szybkość reakcji, ale nadal pozwala uzyskać pełne i precyzyjne wyniki po kompilacji.

## <a name="test-explorer--plus-symbol"></a>Symbol Eksploratora testowego "+" (plus)

**Co oznacza symbol "+" (plus), który pojawia się w górnej linii Eksploratora testów?**

Symbol "+" (plus) wskazuje, że więcej testów może zostać wykrytych po kompilacji po uruchomieniu odnajdowania opartego na zestawie. Ten symbol pojawia się, jeśli dynamicznie zdefiniowane testy zostaną wykryte w projekcie.

![Wiersz podsumowania symbolu Plus](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Odnajdowanie oparte na zestawie

**Odnajdowanie oparte na zestawie nie działa już dla mojego projektu. Jak włączyć go ponownie?**

Przejdź do **Narzędzia** > **Opcje** > **test** i zaznacz pole dodatkowo **odnajdywać testy z zestawów zbudowanych po kompilacjach.**

![Opcja oparta na zestawie](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Odnajdowanie testów w czasie rzeczywistym

**Testy są teraz wyświetlane w Eksploratorze testów podczas pisania, bez konieczności tworzenia projektu. Co się zmieniło?**

Ta funkcja nosi nazwę [odnajdowanie testów w czasie rzeczywistym.](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Używa analizatora Roslyn, aby znaleźć testy i wypełnić Eksploratora testów w czasie rzeczywistym, bez konieczności tworzenia projektu. Aby uzyskać więcej informacji na temat zachowania odnajdywania testów dla dynamicznie zdefiniowanych testów, takich jak teorie lub cechy niestandardowe, zobacz [Odnajdowanie testów dynamicznych](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Zgodność z odnajdowaniami testów w czasie rzeczywistym

**Jakie języki i struktury testowe mogą używać odnajdowania testów w czasie rzeczywistym?**

[Odnajdowanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) działa tylko dla języków zarządzanych (C# i Visual Basic), ponieważ jest ono tworzone przy użyciu kompilatora Roslyn. Na razie odnajdowanie testów w czasie rzeczywistym działa tylko dla platform xUnit, NUnit i MSTest.

## <a name="test-explorer-logs"></a>Dzienniki Eksploratora testów

**Jak włączyć dzienniki eksploratora testów?**

Przejdź do **testu** > **opcji** > narzędzi**i** znajdź tam sekcję Rejestrowanie.

## <a name="uwp-test-discovery"></a>Odnajdowanie testu platformy uniwersalnej systemu zuchw

**Dlaczego moje testy w projektach platformy uniwersalnej systemu i platformy uniwersalnej systemu i nie zostały wykryte, dopóki nie wdrużę aplikacji?**

Testy platformy uniwersalnej systemu Wdrażania docelowe innego środowiska uruchomieniowego, gdy aplikacja jest wdrażana. Oznacza to, że aby znaleźć testy dokładnie dla projektów platformy uniwersalnej systemuświadk.

## <a name="test-explorer-sorting"></a>Sortowanie Eksploratora testów

**Jak działają wyniki testu sortowania w widoku hierarchii?**

Widok hierarchii sortuje testy alfabetycznie, w przeciwieństwie do wyniku. Druga grupa według ustawień zwykle sortuje wyniki testów według wyniku, a następnie alfabetycznie. Zobacz różne grupy według opcji na poniższej ilustracji do porównania. W tym problemie z programem [GitHub](https://github.com/Microsoft/vstest/issues/1425)można przekazać opinię na temat projektu.

![SortowaniePrzyszary](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Widok hierarchii Eksploratora testów

**W widoku hierarchii są przekazywane, nie powiodło się, pominięte i nie uruchamiaj ikony obok grup węzłów nadrzędnych. Co oznaczają te ikony?**

Ikony obok grupowania projektu, obszaru nazw i klas pokazują stan testów w ramach tej grupy. Zobacz poniższą tabelę.

![Ikony hierarchii eksploratora testów](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Wyszukiwanie według ścieżki pliku

**W polu wyszukiwania Eksploratora testów nie ma już filtru "Ścieżka pliku".**

Filtr ścieżki pliku w polu wyszukiwania **Eksploratora testów** został usunięty w programie Visual Studio 2017 w wersji 15.7. Ta funkcja miała niskie użycie, a Eksplorator testów może szybciej pobierać metody testowe, pomijając tę funkcję. Jeśli ta zmiana przerywa przepływ rozwoju, poinformuj nas o tym, przesyłając opinię na temat [społeczności deweloperów.](https://developercommunity.visualstudio.com/)

## <a name="remove-undocumented-interfaces"></a>Usuwanie nieudokumentowanych interfejsów

**Niektóre interfejsy API związane z testami nie są już obecne w programie Visual Studio 2019. Co się zmieniło?**

W programie Visual Studio 2019 niektóre interfejsy API okna testowego, które wcześniej były oznaczone publicznie, ale nigdy nie zostały oficjalnie udokumentowane, zostaną usunięte. Zostały one oznaczone jako "przestarzałe" w programie Visual Studio 2017, aby nadać opiekunom rozszerzeń wczesne ostrzeżenie. Według naszej wiedzy bardzo niewiele rozszerzeń znalazło te interfejsy API i przyjęło zależność od nich. Należą `IGroupByProvider`do `IGroupByProvider<T>` `KeyComparer`nich `ISearchFilter` `ISearchFilterToken`, `ISearchToken`, `SearchFilterTokenType`, , , i . Jeśli ta zmiana ma wpływ na twoje rozszerzenie, poinformuj nas o tym, zgłaszając błąd w [społeczności deweloperów.](https://developercommunity.visualstudio.com)

## <a name="test-adapter-nuget-reference"></a>Odwołanie do karty testowej NuGet

**W programie Visual Studio 2017 w wersji 15.8 moje testy są odnalezione, ale nie są wykonywane.**

Wszystkie projekty testowe muszą zawierać ich .NET test adapter NuGet odwołania w pliku csproj. Jeśli tak nie jest, następujące dane wyjściowe testu są wyświetlane w projekcie, jeśli odnajdowanie przez rozszerzenie karty testowej zostanie uruchomione po kompilacji lub jeśli użytkownik spróbuje uruchomić wybrane testy:

**Projekt {} testowy nie odwołuje się do żadnej karty NuGet .NET. Odnajdowanie lub wykonanie testu może nie działać dla tego projektu. Zaleca się odwoływanie się do kart testowych NuGet w każdym projekcie testowym .NET w rozwiązaniu.**

Zamiast używać rozszerzeń karty testowej, projekty są wymagane do korzystania z pakietów nuget karty testowej. To wymaganie znacznie zwiększa wydajność i powoduje mniej problemów z ciągłej integracji. Więcej informacji na temat wycofania rozszerzenia karty testowej platformy .NET można przeczytać w [informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli używasz karty testowej NUnit 2 i nie możesz przeprowadzić migracji do karty testowej NUnit 3, możesz wyłączyć to nowe zachowanie odnajdywania w programie Visual Studio w wersji 15.8 w**teście****opcji** >  **narzędzi** > .

![Testowanie zachowania karty Eksploratora w opcjach narzędzi](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Nie znaleziono testu platformy uniwersalnej systemuposstw

**Moje testy platformy uniwersalnej systemu i platformy uniwersalnej systemu Wizjudy nie są już wykonywane w programie Visual Studio 2017 w wersji 15.7 i nowszych.**

Najnowsze projekty testów platformy uniwersalnej systemu Windows określają właściwość kompilacji platformy testowej, która umożliwia lepszą wydajność do identyfikowania aplikacji testowych. Jeśli masz projekt testu platformy uniwersalnej systemu i platformy uniwersalnej, który został zainicjowany przed programem Visual Studio w wersji 15.7, ten błąd może zostać wyświetlony w**testach wyjściowych:** **Output** > 

**System.AggregateException: Wystąpił jeden lub więcej błędów. ---> System.InvalidOperationException: W {} witrynie Microsoft.VisualStudio.TestWindow.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

Aby naprawić ten błąd:

- Zaktualizuj właściwość kompilacji projektu testowego przy użyciu następującego kodu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Zaktualizuj wersję SDK testplatform przy użyciu następującego kodu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Używanie flag obiektowych

**Jak włączyć flagi funkcji, aby wypróbować nowe funkcje testowania?**

Flagi funkcji są używane do wysyłki eksperymentalnych lub niedokończonych części produktu do zapalonych użytkowników, którzy chcieliby przekazać opinię przed oficjalnym wysłaniem funkcji. Mogą one zdestabilizować środowisko IDE. Używaj ich tylko w bezpiecznych środowiskach programistujących, takich jak maszyny wirtualne. Flagi funkcji są zawsze używane w ustawieniach własnego ryzyka. Można włączyć funkcje eksperymentalne z [rozszerzeniem flagi funkcji](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)lub za pomocą wiersza polecenia dewelopera.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagę funkcji za pomocą wiersza polecenia dewelopera programu Visual Studio, użyj następującego polecenia. Zmień ścieżkę do miejsca, w którym program Visual Studio jest zainstalowany na komputerze i zmień klucz rejestru na odpowiednią flagę funkcji.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flagę można wyłączyć za pomocą tego samego polecenia, używając wartości 0 zamiast 1 po dword.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Jednostka przetestować swój kod](unit-test-your-code.md)
- [Często zadawane pytania dotyczące testowania jednostek na żywo](live-unit-testing-faq.md)
