---
title: Eksplorator testów — często zadawane pytania
ms.date: 11/07/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8ce8969ecb668d30f87753412dfd53887d050f4c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043573"
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania

## <a name="dynamic-test-discovery"></a>Odnajdywanie testów dynamiczne

**Eksplorator testów nie jest odnajdywanie Moje testy, które są definiowane dynamicznie. (Na przykład teorii, niestandardowych kart, niestandardowe cech, #ifdefs itp.) Jak odnajdywanie, te testy?**

  Skompiluj projekt i upewnij się, odnajdywanie na podstawie zestawu jest włączona w programie **narzędzia** > **opcje** > **testu**.

  [Wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) jest odnajdywanie testów opartych na źródle. Nie można odnaleźć, testy, które korzystają z teorii, niestandardowe karty, niestandardowe cech `#ifdef` instrukcji, a także innych, ponieważ są one definiowane w czasie wykonywania. Kompilacja jest wymagana dla tych testów, aby znaleźć dokładnie. W programie Visual Studio 2017 w wersji 15.6 i nowszych opartych na zestawie odnajdywania (wykrywacz tradycyjnych) działa tylko po kompilacji. To ustawienie znajduje odnajdywania testów w czasie rzeczywistym oznacza dowolną liczbę testów, jak to możliwe, podczas edytowania i odnajdywanie na podstawie zestawu umożliwia dynamicznie definiowane testów są wyświetlane po kompilacji. Wykrywanie testów w czasie rzeczywistym poprawia czas odpowiedzi, ale aparaturze pozwala uzyskać kompletne i dokładne wyniki po kompilacji.

## <a name="test-explorer--plus-symbol"></a>Eksplorator testów "+" (plus) symbol

**Co to jest "+" (plus) symbol, który pojawia się w górnej linii średniej Eksploratora testów?**

  "+" (Plus) symbol informuje, że może zostać odnalezionych więcej testów po kompilacji tak długo, jak odnajdywanie na podstawie zestawu jest włączona. Ten symbol zostanie wyświetlony w przypadku definiowane dynamicznie testy zostaną wykryte w projekcie.

  ![Symbol wiersz podsumowania plus](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Odnajdywanie na podstawie zestawu

**Odnajdywanie na podstawie zestawu już nie działa dla mojego projektu. Jak włączyć go ponownie?**

  Przejdź do **narzędzia** > **opcje** > **testu** i pole wyboru dla **dodatkowo odnajduj testy z poziomu skompilowanych zestawów po kompilacje.**

  ![Na podstawie zestawu opcji](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Wykrywanie testów w czasie rzeczywistym

**Testy są wyświetlane w Eksploratorze testów podczas pisania, bez konieczności tworzenia projektu. Co się zmieniło?**

  Ta funkcja jest nazywana [wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824). Użyto analizatora Roslyn można znaleźć testy i wypełnić Eksplorator testów w czasie rzeczywistym bez konieczności kompilowania projektu. Aby uzyskać więcej informacji o zachowaniu odnajdywania testów dla dynamicznie definiowane testów, takich jak TEORIE lub cechy niestandardowych zobacz często zadawane pytania dotyczące nr 1.

## <a name="real-time-test-discovery-compatibility"></a>Zgodność odnajdywania testów w czasie rzeczywistym

**Jakich języków i środowisk testowych można użyć odnajdywaniem testów w czasie rzeczywistym?**

  [Wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) działa tylko w przypadku języków zarządzanych (C# i Visual Basic), ponieważ jest zbudowany za pomocą kompilatora Roslyn. Na razie wykrywanie testów w czasie rzeczywistym działa tylko w przypadku xUnit, NUnit oraz MSTest struktur.

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

**W widoku hierarchii zostaną przekazane, zakończone niepowodzeniem, pominięto i nie uruchomiono ikony obok projektu, Namespace i klasa grupowania. Co oznaczają ikony**

  Ikony obok projektu, Namespace i klasa grupowania wyświetlić stan testów w ramach tej grupy. Zobacz poniższą tabelę.

  ![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Wyszukaj według ścieżki pliku

**Nie ma już filtru "Ścieżka pliku" w polu wyszukiwania Eksploratora testów.**

Filtr ścieżki pliku w **Eksplorator testów** pole wyszukiwania została usunięta w wersji 15.7 programu Visual Studio 2017 w wersji zapoznawczej 3. Ta funkcja była o niskim użyciu i Eksplorator testów może pobrać szybszych metod testowych, pomijając tej funkcji. Daj nam znać, jeśli ta zmiana przerywa przepływ rozwoju, przesyłając swoje opinie na [społeczności deweloperów](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Usuń nieudokumentowane interfejsy

**Niektóre interfejsy API związane z testów nie są już dostępne w programie Visual Studio 2019 r. Co się zmieniło?**

W programie Visual Studio 2019 r niektóre okna testów interfejsów API, które wcześniej zostały oznaczone jako publiczne, ale nigdy nie jest oficjalnie zostały udokumentowane zostaną usunięte. Zostały one oznaczone jako "przestarzałe" w programie Visual Studio 2017 pozwala maintainers rozszerzenia wczesnego ostrzegania. Do naszej wiedzy bardzo mało rozszerzenia ma znaleźć tych interfejsów API i wykonywanych zależności na nich. Obejmują one `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken`, i `SearchFilterTokenType`. Daj nam znać, jeśli ta zmiana ma wpływ na Twoje rozszerzenie, wypełniając usterki na [społeczności deweloperów](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Adapter testowy odwołań NuGet

**W programie Visual Studio 2017 wersja 15.8 Moje testy są odnajdywane, ale nie wykonywania.**

Wszystkie projekty testowe mogą zawierać adapter testowy ich .NET NuGet odwołania w pliku csproj. Jeśli nie, jeśli odnajdywania przez rozszerzenie adaptera testowego jest rozpoczęła się po kompilacji, lub jeśli użytkownik próbuje uruchomić wybranych testów w projekcie pojawia się następujące dane wyjściowe testu:

**Projekt testowy {} nie odwołuje się do dowolnej karty NuGet programu .NET. Odnajdywanie lub wykonywanie testów może nie działać w przypadku tego projektu. Zaleca się odwołań NuGet adapterów testowych w każdym projekcie testów platformy .NET w rozwiązaniu.**

Zamiast korzystać z rozszerzeń adaptera testowego, projekty są wymagane do korzystania z pakietów NuGet adaptera testowego. Wymaganie to znacznie zwiększa wydajność i powoduje, że mniej problemów dzięki ciągłej integracji. Przeczytaj więcej na temat rozszerzenia Adapter testu .NET jest przestarzała w [informacje o wersji](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

> [!NOTE]
> Jeśli używasz rozszerzenie NUnit 2 Test Adapter i nie mogą przeprowadzić migrację do NUnit 3 test adapter, możesz wyłączyć to nowe zachowanie odnajdywania w programie Visual Studio w wersji 15.8 w **narzędzia** > **opcje**  >  **Testu**.

  ![Testowanie zachowania Eksploratora karty w opcjach narzędzi](media/testex-adapterbehavior.png)

## <a name="uwp-testcontainer-was-not-found"></a>Nie można odnaleźć TestContainer platformy uniwersalnej systemu Windows

**Moje testy platformy uniwersalnej systemu Windows nie są wykonywane w programie Visual Studio 2017 w wersji 15.7 lub nowszej.**

Ostatnie projekty testowe platformy uniwersalnej systemu Windows, określ właściwość kompilacji platformy testu, która pozwala zwiększyć wydajność do identyfikowania aplikacje testowe. W przypadku projektu testowego platformy uniwersalnej systemu Windows, który został zainicjowany przed Visual Studio w wersji 15.7 może zostać wyświetlony ten błąd wystąpił w **dane wyjściowe** > **testy**:

**System.AggregateException: Wystąpił co najmniej jednego błędu. ---> System.InvalidOperationException: Nie można odnaleźć następującego obiektu TestContainer {} na Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider <GetTestContainerAsync>d__61.MoveNext()**

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
