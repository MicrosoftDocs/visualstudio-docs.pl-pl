---
title: Eksplorator testów — często zadawane pytania
description: Zapoznaj się z tymi często zadawanych pytań dotyczących Visual Studio Test Explorer, które obejmują niektóre typowe procedury rozwiązywania problemów.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
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
manager: jmartens
ms.openlocfilehash: 22ac969ba2ad918fcbeb7c53e04cd3f2b03a0431
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798573"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Eksplorator testów — często zadawane pytania

## <a name="dynamic-test-discovery"></a>Odnajdywanie testów dynamicznych

**Eksplorator testów nie odnajduje moich testów, które są definiowane dynamicznie. (Na przykład teorie, karty niestandardowe, cechy niestandardowe, #ifdefs itp.) Jak mogę odnaleźć te testy?**

::: moniker range=">=vs-2019"
Skompilowanie projektu w celu uruchomienia odnajdywania opartego na zestawie.
::: moniker-end
::: moniker range="vs-2017"
Skompilować projekt i upewnić się, że  odnajdywanie oparte na zestawie jest włączone w > **narzędziu Opcje** > **Testuj.**
::: moniker-end
[Odnajdywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) jest oparte na źródle. Nie może odnajdywać testów, które używają teorii, kart niestandardowych, niestandardowych cech, instrukcji i innych, ponieważ są one definiowane `#ifdef` w czasie uruchamiania. Aby te testy zostały dokładnie znalezione, wymagana jest kompilacja. W Visual Studio 2017 r. w wersji 15.6 lub nowszej odnajdywanie oparte na zestawie (tradycyjny program odnajdywania) jest uruchamiane tylko po kompilacji. To ustawienie oznacza, że odnajdywanie testów w czasie rzeczywistym znajduje tyle testów, ile jest w trakcie edytowania, a odnajdywanie oparte na zestawie umożliwia dynamiczne pojawianie się testów po kompilacji. Odnajdywanie testów w czasie rzeczywistym poprawia czas odpowiedzi, ale nadal umożliwia uzyskiwanie pełnych i dokładnych wyników po kompilacji.

## <a name="test-explorer--plus-symbol"></a>Symbol "+" (plus) eksploratora testów

**Co oznacza symbol "+" (plus), który pojawia się w górnym wierszu Eksploratora testów?**

Symbol "+" (plus) wskazuje, że po kompilacji po zakończeniu odnajdywania opartego na zestawie można wykryć więcej testów. Ten symbol jest wyświetlany, jeśli w projekcie zostaną wykryte dynamicznie zdefiniowane testy.

![Znak plus symbolu wiersz podsumowania](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Odnajdywanie oparte na zestawie

**Odnajdywanie oparte na zestawie nie działa już w moim projekcie. Jak mogę ją ponownie włączyć?**

Przejdź do **opcji** narzędzia Test i zaznacz pole wyboru Dodatkowo odnajduj testy z zestawów skompilowanych >  >  **po kompilacjach.**

![Opcja oparta na zestawie](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Odnajdywanie testów w czasie rzeczywistym

**Testy są teraz wyświetlane w Eksploratorze testów podczas wpisywania bez konieczności kompilowania projektu. Co się zmieniło?**

Ta funkcja jest [nazywana odnajdywaniem testów w czasie rzeczywistym.](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Używa analizatora Roslyn do wyszukiwania testów i wypełniania Eksploratora testów w czasie rzeczywistym, bez konieczności kompilowania projektu. Aby uzyskać więcej informacji na temat zachowania odnajdywania testów dla dynamicznie zdefiniowanych testów, takich jak teorie lub niestandardowe cechy, zobacz [Dynamiczne odnajdywanie testów](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Zgodność odnajdywania testów w czasie rzeczywistym

**Jakie języki i struktury testowe mogą używać odnajdywania testów w czasie rzeczywistym?**

[Odnajdywanie testów w](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) czasie rzeczywistym działa tylko w przypadku języków zarządzanych (C# i Visual Basic), ponieważ jest ono zbudowane przy użyciu kompilatora Roslyn. Na razie odnajdywanie testów w czasie rzeczywistym działa tylko w przypadku platform xUnit, NUnit i MSTest.

## <a name="test-explorer-logs"></a>Dzienniki Eksploratora testów

**Jak mogę włączyć dzienniki dla Eksploratora testów?**

Przejdź do **opcji**  >    >  **narzędzia Test** i znajdź sekcję Rejestrowanie.

## <a name="uwp-test-discovery"></a>Odnajdywanie testów platformy uniwersalnej systemu Windows

**Dlaczego moje testy w projektach platformy uniwersalnej systemu Windows nie są odnalezione, dopóki nie wdaję aplikacji?**

Testy platformy uniwersalnej systemu Windows mają na celu inne środowisko uruchomieniowe podczas wdrażania aplikacji. Oznacza to, że dokładne znalezienie testów dla projektów platformy UWP wymaga nie tylko skompilowania projektu, ale również wdrożenia.

## <a name="test-explorer-sorting"></a>Sortowanie w Eksploratorze testów

**Jak działa sortowanie wyników testów w widoku hierarchii?**

Widok hierarchii sortuje testy alfabetycznie, a nie według wyniku. Poprzednie grupowanie według ustawień posortowało wyniki testu według wyniku, a następnie alfabetycznie. Nadal możesz włączyć sortowanie według wyniku, klikając prawym przyciskiem myszy nagłówek kolumny w Eksploratorze testów, włączając kolumnę State, a następnie klikając nagłówek Kolumna stanu, aby zastosować sortowanie dla tej kolumny. Możesz przekazać opinię na temat projektu w tym problemie [w usłudze GitHub.](https://github.com/Microsoft/vstest/issues/1425)

## <a name="test-explorer-hierarchy-view"></a>Widok hierarchii Eksploratora testów

**W widoku hierarchii obok grup węzłów nadrzędnych znajdują się ikony przekazywane, pomijane, pomijane i nie uruchamiania. Co oznaczają te ikony?**

Ikony obok grupowania Projekt, Przestrzeń nazw i Klasa pokazują stan testów w ramach tego grupowania. Zobacz poniższą tabelę.

![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Wyszukiwanie według ścieżki pliku

**W polu wyszukiwania Eksplorator testów nie ma już filtru "Ścieżka pliku".**

Filtr ścieżki pliku w polu wyszukiwania **Eksplorator testów** został usunięty w wersji 15.7 Visual Studio 2017. Ta funkcja miała niskie użycie, a Eksplorator testów może szybciej pobierać metody testowe, pomijając tę funkcję. Jeśli ta zmiana przerywa przepływ tworzenia aplikacji, daj nam znać, przesyłając opinię na [Developer Community.](https://aka.ms/feedback/suggest?space=8)

## <a name="remove-undocumented-interfaces"></a>Usuwanie nieudokumentowanych interfejsów

**Niektóre interfejsy API związane z testami nie są już dostępne w Visual Studio 2019 r. Co się zmieniło?**

W Visual Studio 2019 r. niektóre interfejsy API okna testowego, które wcześniej były oznaczone jako publiczne, ale nigdy nie były oficjalnie udokumentowane, zostaną usunięte. Zostały one oznaczone jako "przestarzałe" w Visual Studio 2017 r., aby zapewnić obsługi rozszerzeń wczesne ostrzeżenie. Z naszej wiedzy bardzo niewiele rozszerzeń znalazło te interfejsy API i było od nich zależne. Należą do `IGroupByProvider` nich , , , , , i `IGroupByProvider<T>` `KeyComparer` `ISearchFilter` `ISearchFilterToken` `ISearchToken` `SearchFilterTokenType` . Jeśli ta zmiana ma wpływ na Twoje rozszerzenie, daj nam znać, zgłaszanie usterki w [Developer Community](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Odwołanie NuGet adaptera testowego

**W Visual Studio 2017 w wersji 15.8 moje testy zostały odnalezione, ale nie są wykonywane.**

Wszystkie projekty testowe muszą zawierać odwołanie NuGet adaptera testowego .NET w pliku csproj. Jeśli tak się nie stanie, w projekcie zostaną wyświetlone następujące dane wyjściowe testu, jeśli odnajdywanie przez rozszerzenie adaptera testowego rozpocznie się po kompilacji lub jeśli użytkownik spróbuje uruchomić wybrane testy:

**Projekt {} testowy nie odwołuje się do żadnej karty NuGet .NET. Odnajdywanie lub wykonywanie testów może nie działać w tym projekcie. Zaleca się odwołanie do adapterów testowych NuGet w każdym projekcie testowym .NET w rozwiązaniu.**

Zamiast używać rozszerzeń adaptera testowego, projekty są wymagane do korzystania z pakietów NuGet adaptera testowego. To wymaganie znacznie zwiększa wydajność i powoduje mniejszą liczbę problemów z ciągłą integracją. Przeczytaj więcej na temat cofania wersji rozszerzenia adaptera testowego .NET w [informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli używasz adaptera testowego NUnit 2 i nie możesz przeprowadzić migracji do adaptera testowego NUnit 3, możesz wyłączyć to nowe zachowanie odnajdywania w programie Visual Studio w wersji 15.8 w teście Narzędzia Opcje  >    >  .

![Zachowanie adaptera Eksploratora testów w opcjach narzędzi](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Nie znaleziono aplikacji TestContainer platformy uniwersalnej systemu Windows

**Moje testy platformy uniwersalnej systemu Windows nie są już wykonywane w Visual Studio 2017 w wersji 15.7 i nowszych.**

Ostatnie projekty testowe platformy uniwersalnej systemu Windows określają właściwość kompilacji platformy testowej, która umożliwia lepszą wydajność identyfikowania aplikacji testowych. Jeśli masz projekt testowy platformy uniwersalnej systemu Windows, który został zainicjowany przed wersją Visual Studio 15.7, w testach **wyjściowych** może zostać wyświetlony ten  >  **błąd:**

**System.AggregateException: Wystąpił co najmniej jeden błąd. ---> System.InvalidOperationException: W aplikacji {} Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider nie znaleziono następującego \<GetTestContainerAsync> d__61.MoveNext()**

Aby naprawić ten błąd:

- Zaktualizuj właściwość kompilacji projektu testowego przy użyciu następującego kodu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Zaktualizuj wersję zestawu SDK Platformy TestPlatform przy użyciu następującego kodu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Korzystanie z funkcji w wersji zapoznawczej

W Visual Studio 2019 r. możesz wybrać funkcje w wersji zapoznawczej w narzędziu **Narzędzia > Opcje > Environment > wersji zapoznawczej.**
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Używanie flag funkcji

**Jak mogę włączyć flagi funkcji, aby wypróbować nowe funkcje testowania?**

Flagi funkcji są używane do wysłania eksperymentalnych lub niedokończonych części produktu do zapalonych użytkowników, którzy chcą przekazać opinię, zanim funkcje zostaną oficjalnie nadane. Mogą one zdestabilizować środowisko IDE. Należy ich używać tylko w bezpiecznych środowiskach programistycznych, takich jak maszyny wirtualne. Flagi funkcji są zawsze ustawieniami własnego ryzyka. Funkcje eksperymentalne można włączyć z rozszerzeniem [flag funkcji lub](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)za pomocą wiersza polecenia dewelopera.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagę funkcji za pomocą Visual Studio wiersza polecenia dla deweloperów, użyj następującego polecenia. Zmień ścieżkę na miejsce Visual Studio na komputerze, a następnie zmień klucz rejestru na flagę funkcji, której chcesz użyć.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flagę można wyłączyć za pomocą tego samego polecenia, używając wartości 0 zamiast 1 po dword.
::: moniker-end
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](/previous-versions/dd293546(v=vs.110))
- [Testowanie jednostkowe kodu](unit-test-your-code.md)
- [Testy jednostkowe na żywo — często zadawane pytania](live-unit-testing-faq.yml)