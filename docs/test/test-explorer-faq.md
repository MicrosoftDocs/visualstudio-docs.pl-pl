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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846807"
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Gdzie jest Grupuj według cech w programie Visual Studio 2019?
Ta grupa cech została przeniesiona jako kolumna. W przypadku hierarchii z obsługą wielowarstwową i dostosowywalną w programie Visual Studio 2019 w wersji 16,2, firma Microsoft uważa, że cechy takie jak tworzenie grup nie wymagały złożoności wizualnej. Oczekujemy na opinię na temat tego projektu. https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Na razie możesz kliknąć prawym przyciskiem myszy kolumnę w Eksploratorze testów i wybrać kolumny. Sprawdź kolumnę cech i pojawi się w Eksploratorze testów. Teraz można filtrować tę kolumnę według interesujących Cię cech.

![wyświetlić](media/vs-2019/trait-column.png)
kolumny cech ![filtrowanie kolumny cech](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Odnajdywanie testów dynamiczne

**Eksplorator testów nie odnajduje moich testów, które są definiowane dynamicznie. (Na przykład teorie, niestandardowe karty, cechy niestandardowe, #ifdefs itd.) Jak można odnaleźć te testy?**

::: moniker range=">=vs-2019"
Skompiluj projekt, aby uruchomić odnajdywanie oparte na zestawie.
::: moniker-end
::: moniker range="vs-2017"
Skompiluj projekt i upewnij się, że odnajdywanie oparte na zestawie jest włączone w **narzędziu** > **Opcje** > **test**.
::: moniker-end
[Wykrywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) jest odnajdywanie testów opartych na źródle. Nie mogą odnajdywać testów korzystających z teorie, niestandardowych kart sieciowych, cech niestandardowych, instrukcji `#ifdef` i innych, ponieważ są one zdefiniowane w czasie wykonywania. Kompilacja jest wymagana dla tych testów, aby znaleźć dokładnie. W programie Visual Studio 2017 w wersji 15.6 i nowszych opartych na zestawie odnajdywania (wykrywacz tradycyjnych) działa tylko po kompilacji. To ustawienie znajduje odnajdywania testów w czasie rzeczywistym oznacza dowolną liczbę testów, jak to możliwe, podczas edytowania i odnajdywanie na podstawie zestawu umożliwia dynamicznie definiowane testów są wyświetlane po kompilacji. Wykrywanie testów w czasie rzeczywistym zwiększa czas odpowiedzi, ale nadal umożliwia uzyskanie pełnych i precyzyjnych wyników po kompilacji.

## <a name="test-explorer--plus-symbol"></a>Eksplorator testów "+" (plus) symbol

**Co to jest "+" (plus) symbol, który pojawia się w górnej linii średniej Eksploratora testów?**

Symbol "+" (plus) wskazuje, że więcej testów może zostać odnalezione po kompilacji podczas uruchamiania odnajdywania opartego na zestawach. Ten symbol zostanie wyświetlony w przypadku definiowane dynamicznie testy zostaną wykryte w projekcie.

![Symbol wiersz podsumowania plus](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Odnajdywanie na podstawie zestawu

**Odnajdywanie oparte na zestawie nie działa już w projekcie. Jak mogę włączyć ją ponownie?**

Przejdź do pozycji **narzędzia** > **Opcje** > **Testuj** i zaznacz pole wyboru, aby **dodatkowo wykrywać testy z skompilowanych zestawów po kompilacji.**

![Na podstawie zestawu opcji](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Wykrywanie testów w czasie rzeczywistym

**Testy są teraz wyświetlane w Eksploratorze testów podczas wpisywania, bez konieczności kompilowania projektu. Co się zmieniło?**

Ta funkcja jest nazywana [wykrywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Użyto analizatora Roslyn można znaleźć testy i wypełnić Eksplorator testów w czasie rzeczywistym bez konieczności kompilowania projektu. Aby uzyskać więcej informacji na temat zachowania odnajdywania testów dla dynamicznie zdefiniowanych testów, takich jak teorie lub cechy niestandardowe, zobacz [odnajdywanie testów dynamicznych](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Zgodność odnajdywania testów w czasie rzeczywistym

**Jakich języków i środowisk testowych można użyć odnajdywaniem testów w czasie rzeczywistym?**

[Wykrywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) działa tylko w przypadku języków zarządzanych (C# i Visual Basic), ponieważ jest zbudowany za pomocą kompilatora Roslyn. Na razie wykrywanie testów w czasie rzeczywistym działa tylko w przypadku xUnit, NUnit oraz MSTest struktur.

## <a name="test-explorer-logs"></a>Dzienniki narzędzia Eksplorator testów

**Jak można włączyć dzienniki dla Eksploratora testów?**

Przejdź do **narzędzia** > **opcje** > **testu** i znaleźć w sekcji rejestrowanie.

## <a name="uwp-test-discovery"></a>Odnajdywanie testów platformy uniwersalnej systemu Windows

**Dlaczego są moje testy w projektach platformy uniwersalnej systemu Windows, które nie zostało wykryte do momentu czy mogę wdrożyć mojej aplikacji?**

Testy platformy uniwersalnej systemu Windows przeznaczone różne środowiska uruchomieniowego, gdy aplikacja jest wdrożona. Oznacza to, aby znaleźć testy dokładnie dla projektów platformy UWP nie tylko konieczność Skompiluj projekt, ale także wdrożyć.

## <a name="test-explorer-sorting"></a>Test Explorer sortowania

**Jak działa sortowania wyników testów w widoku hierarchii**

Widok hierarchii sortowania testy alfabetycznie w przeciwieństwie do wyników. Grupy za pomocą ustawień zwykle sortować wyniki testów według wyników i następnie alfabetycznie. Aby wyświetlić innej grupy opcji na poniższej ilustracji do porównania. Możesz przekazywać opinie dotyczące projektowania [ten problem usługi GitHub](https://github.com/Microsoft/vstest/issues/1425).

![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Widok hierarchii Eksploratora testów

**W widoku hierarchia są wyświetlane ikony "zakończone niepowodzeniem, pominięte" i nie są uruchamiane obok grup węzłów nadrzędnych. Co oznaczają te ikony?**

Ikony obok projektu, Namespace i klasa grupowania wyświetlić stan testów w ramach tej grupy. Zobacz poniższą tabelę.

![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Wyszukaj według ścieżki pliku

**Nie ma już filtru "Ścieżka pliku" w polu wyszukiwania Eksploratora testów.**

Filtr ścieżka pliku w polu wyszukiwania programu **Test Explorer** został usunięty z programu Visual Studio 2017 w wersji 15,7. Ta funkcja ma niskie użycie i Eksplorator testów może szybciej pobrać metody testowe, pozostawiając tę funkcję. Daj nam znać, jeśli ta zmiana przerywa przepływ rozwoju, przesyłając swoje opinie na [społeczności deweloperów](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Usuń nieudokumentowane interfejsy

**Niektóre interfejsy API związane z testami nie są już obecne w programie Visual Studio 2019. Co się zmieniło?**

W programie Visual Studio 2019 r niektóre okna testów interfejsów API, które wcześniej zostały oznaczone jako publiczne, ale nigdy nie jest oficjalnie zostały udokumentowane zostaną usunięte. Zostały one oznaczone jako "przestarzałe" w programie Visual Studio 2017 pozwala maintainers rozszerzenia wczesnego ostrzegania. Do naszej wiedzy bardzo mało rozszerzenia ma znaleźć tych interfejsów API i wykonywanych zależności na nich. Obejmują one `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken`, i `SearchFilterTokenType`. Daj nam znać, jeśli ta zmiana ma wpływ na Twoje rozszerzenie, wypełniając usterki na [społeczności deweloperów](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Adapter testowy odwołań NuGet

**W programie Visual Studio 2017 wersja 15.8 Moje testy są odnajdywane, ale nie wykonywania.**

Wszystkie projekty testowe mogą zawierać adapter testowy ich .NET NuGet odwołania w pliku csproj. Jeśli nie, jeśli odnajdywania przez rozszerzenie adaptera testowego jest rozpoczęła się po kompilacji, lub jeśli użytkownik próbuje uruchomić wybranych testów w projekcie pojawia się następujące dane wyjściowe testu:

**{} projektu testowego nie odwołuje się do żadnej karty NuGet programu .NET. Odnajdywanie lub wykonywanie testów może nie zadziałało dla tego projektu. Zalecane jest odwoływanie się do adapterów testowych NuGet w każdym projekcie testowym .NET w rozwiązaniu.**

Zamiast korzystać z rozszerzeń adaptera testowego, projekty są wymagane do korzystania z pakietów NuGet adaptera testowego. Wymaganie to znacznie zwiększa wydajność i powoduje, że mniej problemów dzięki ciągłej integracji. Przeczytaj więcej na temat rozszerzenia Adapter testu .NET jest przestarzała w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli używasz rozszerzenie NUnit 2 Test Adapter i nie mogą przeprowadzić migrację do NUnit 3 test adapter, możesz wyłączyć to nowe zachowanie odnajdywania w programie Visual Studio w wersji 15.8 w **narzędzia** > **opcje**  >  **Testu**.

![Testowanie zachowania Eksploratora karty w opcjach narzędzi](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Nie można odnaleźć TestContainer platformy uniwersalnej systemu Windows

**Moje testy platformy UWP nie są już wykonywane w programie Visual Studio 2017 w wersji 15,7 lub nowszej.**

Ostatnie projekty testowe platformy uniwersalnej systemu Windows, określ właściwość kompilacji platformy testu, która pozwala zwiększyć wydajność do identyfikowania aplikacje testowe. W przypadku projektu testowego platformy uniwersalnej systemu Windows, który został zainicjowany przed Visual Studio w wersji 15.7 może zostać wyświetlony ten błąd wystąpił w **dane wyjściowe** > **testy**:

**System. AggregateException: wystąpił co najmniej jeden błąd. ---> System. InvalidOperationException: nie znaleziono następującego TestContaineru {} w firmie Microsoft. VisualStudio. TestWindow. Controller. TestContainerProvider \<GetTestContainerAsync > d__61. MoveNext ()**

Aby naprawić ten błąd:

- Zaktualizuj właściwości kompilacji projektu testu przy użyciu następującego kodu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualizacja wersji zestawu SDK TestPlatform, używając następującego kodu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Przy użyciu flag funkcji

**Jak można włączyć flagi funkcji, aby wypróbować nowe funkcje testowania?**

Flagi funkcji są używane na potrzeby wysłania eksperymentalne lub niedokończone części produktu avid użytkownikom, którzy chcieliby przesłać opinię, zanim funkcje dostarczanie oficjalnie. Mogą one zdestabilizować środowiska IDE. Ich używać tylko w środowiskach programowania bezpiecznych, takich jak maszyny wirtualne. Flagi funkcji są zawsze Użyj your-own zagrożonej ustawienia. Można włączyć funkcji eksperymentalnych, za pomocą [flagi funkcji rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), lub za pomocą wiersza polecenia dla deweloperów.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagi funkcji za pomocą wiersza polecenia dla deweloperów programu Visual Studio, użyj następującego polecenia. Zmień ścieżkę, na którym zainstalowano program Visual Studio na komputerze, a do flagę funkcji, które chcesz zmienić wartość klucza rejestru.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flaga przy użyciu tego samego polecenia, można wyłączyć przy użyciu wartości 0 zamiast 1 po typu dword.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Kod testu jednostkowego](unit-test-your-code.md)
- [Testowanie jednostek — często zadawane pytania na żywo](live-unit-testing-faq.md)
