---
title: Eksplorator testów — często zadawane pytania
description: Zapoznaj się z często zadawanymi pytaniami dotyczącymi programu Visual Studio Test Explorer, które obejmują pewne typowe Rozwiązywanie problemów.
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
ms.openlocfilehash: a1e0f998b5fff45a8fee9ac6f9cc6a0ce2268907
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894468"
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania

## <a name="dynamic-test-discovery"></a>Odnajdywanie testów dynamicznych

**Eksplorator testów nie odnajduje moich testów, które są definiowane dynamicznie. (Na przykład teorie, niestandardowe karty, cechy niestandardowe, #ifdefs itd.) Jak można odnaleźć te testy?**

::: moniker range=">=vs-2019"
Skompiluj projekt, aby uruchomić odnajdywanie oparte na zestawie.
::: moniker-end
::: moniker range="vs-2017"
Skompiluj projekt i upewnij się, że odnajdywanie oparte na zestawie jest włączone  w >  > **test** Options Tools.
::: moniker-end
[Wykrywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) jest odnajdywaniem testów opartym na źródle. Nie można wykryć testów, które używają teorie, niestandardowych kart, cech niestandardowych, `#ifdef` instrukcji i innych, ponieważ są one zdefiniowane w czasie wykonywania. Dla tych testów jest wymagana kompilacja. W programie Visual Studio 2017 w wersji 15,6 lub nowszej odnajdywanie oparte na zestawie (tradycyjny program Discovery) działa tylko po kompilacji. To ustawienie oznacza, że funkcja odnajdywania testów w czasie rzeczywistym znajduje tyle testów, ile jest w trakcie edycji, a funkcja odnajdywania oparta na zestawach umożliwia dynamiczne Definiowanie testów, które są wyświetlane po kompilacji. Wykrywanie testów w czasie rzeczywistym zwiększa czas odpowiedzi, ale nadal umożliwia uzyskanie pełnych i precyzyjnych wyników po kompilacji.

## <a name="test-explorer--plus-symbol"></a>Symbol programu Test Explorer ' + ' (plus)

**Co oznacza symbol "+" (plus), który pojawia się w górnej linii Eksploratora testów?**

Symbol "+" (plus) wskazuje, że więcej testów może zostać odnalezione po kompilacji podczas uruchamiania odnajdywania opartego na zestawach. Ten symbol pojawia się, jeśli w projekcie wykryto dynamiczne zdefiniowane testy.

![Linia podsumowania symboli Plus](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Odnajdywanie oparte na zestawie

**Odnajdywanie oparte na zestawie nie działa już w projekcie. Jak mogę włączyć ją ponownie?**

Przejdź do pozycji **Narzędzia** > **Opcje** > **test** i zaznacz pole wyboru **Odnajdź testy od skompilowanych zestawów po kompilacji.**

![Opcja oparta na zestawie](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Wykrywanie testów w czasie rzeczywistym

**Testy są teraz wyświetlane w Eksploratorze testów podczas wpisywania, bez konieczności kompilowania projektu. Co się zmieniło?**

Ta funkcja jest nazywana [odnajdywaniem testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Używa analizatora Roslyn do znajdowania testów i wypełniania Eksploratora testów w czasie rzeczywistym, bez konieczności kompilowania projektu. Aby uzyskać więcej informacji na temat zachowania odnajdywania testów dla dynamicznie zdefiniowanych testów, takich jak teorie lub cechy niestandardowe, zobacz [odnajdywanie testów dynamicznych](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Zgodność z odnajdywaniem testów w czasie rzeczywistym

**Jakie języki i platformy testowe mogą korzystać z odnajdywania testów w czasie rzeczywistym?**

[Wykrywanie testów w czasie rzeczywistym](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) działa tylko w przypadku języków zarządzanych (C# i Visual Basic), ponieważ zostały skompilowane przy użyciu kompilatora Roslyn. Obecnie wykrywanie testów w czasie rzeczywistym działa tylko dla platform xUnit, NUnit i MSTest.

## <a name="test-explorer-logs"></a>Dzienniki Eksploratora testów

**Jak włączyć dzienniki dla Eksploratora testów?**

Przejdź do   >  **opcji** narzędzia  >  **testy** i Znajdź sekcję rejestrowanie.

## <a name="uwp-test-discovery"></a>Odnajdywanie testów platformy UWP

**Dlaczego moje testy w projektach platformy UWP nie zostały odnalezione przed wdrożeniem mojej aplikacji?**

Testy platformy UWP są ukierunkowane na inne środowisko uruchomieniowe, gdy aplikacja jest wdrażana. Oznacza to, że aby znaleźć testy dokładnie dla projektów platformy UWP, które nie są potrzebne tylko do skompilowania projektu, ale również do wdrożenia.

## <a name="test-explorer-sorting"></a>Sortowanie Eksploratora testów

**Jak sortowanie wyników testów działa w widoku hierarchii?**

Widok hierarchii sortuje testy alfabetycznie, w przeciwieństwie do wyników. Poprzednia Grupa według ustawień posortować wyniki testów według wyniku, a następnie alfabetycznie. Można nadal włączać sortowanie według wyniku, klikając prawym przyciskiem myszy nagłówek kolumny w Eksploratorze testów, włączając kolumnę State, a następnie klikając nagłówek kolumny State, aby zastosować sortowanie dla tej kolumny. Możesz przekazać opinię na temat projektu w tym [wydaniu usługi GitHub](https://github.com/Microsoft/vstest/issues/1425).

## <a name="test-explorer-hierarchy-view"></a>Widok hierarchii Eksploratora testów

**W widoku hierarchia są wyświetlane ikony "zakończone niepowodzeniem, pominięte" i nie są uruchamiane obok grup węzłów nadrzędnych. Co oznaczają te ikony?**

Ikony obok projektu, obszaru nazw i grup klas przedstawiają stan testów w ramach tego grupowania. Zobacz poniższą tabelę.

![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Wyszukaj według ścieżki pliku

**W polu wyszukiwania Eksploratora testów nie ma już filtru "ścieżka do pliku".**

Filtr ścieżka pliku w polu wyszukiwania programu **Test Explorer** został usunięty z programu Visual Studio 2017 w wersji 15,7. Ta funkcja ma niskie użycie i Eksplorator testów może szybciej pobrać metody testowe, pozostawiając tę funkcję. Jeśli ta zmiana przerwie przepływ tworzenia, powiadom nas o przesłaniu opinii na temat [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).

## <a name="remove-undocumented-interfaces"></a>Usuń nieudokumentowane interfejsy

**Niektóre interfejsy API związane z testami nie są już obecne w programie Visual Studio 2019. Co się zmieniło?**

W programie Visual Studio 2019 niektóre interfejsy API okna testowego, które zostały wcześniej oznaczone jako publiczne, ale nigdy nie zostały oficjalnie udokumentowane, zostaną usunięte. Zostały one oznaczone jako "przestarzałe" w programie Visual Studio 2017, aby zapewnić obsłudze rozszerzenia wczesne ostrzeżenie. W naszej wiedzy bardzo kilka rozszerzeń odnalazło te interfejsy API i pobrano od nich zależność. Należą `IGroupByProvider` do nich, `IGroupByProvider<T>` ,,,, `KeyComparer` `ISearchFilter` `ISearchFilterToken` `ISearchToken` i `SearchFilterTokenType` . Jeśli ta zmiana wpłynie na Twoje rozszerzenie, poinformuj nas o błędzie w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Dokumentacja NuGet adaptera testowego

**W programie Visual Studio 2017 w wersji 15,8 moje testy zostały wykryte, ale nie są wykonywane.**

Wszystkie projekty testowe muszą zawierać w pliku csproj swoje odwołanie NuGet do adaptera testowego platformy .NET. Jeśli nie, następujące dane wyjściowe testu pojawiają się w projekcie, jeśli odnajdywanie przez rozszerzenie adaptera testowego zostanie uruchomione po kompilacji lub użytkownik próbuje uruchomić wybrane testy:

**Projekt testowy {} nie odwołuje się do żadnej karty NuGet programu .NET. Odnajdywanie lub wykonywanie testów może nie zadziałało dla tego projektu. Zalecane jest odwoływanie się do adapterów testowych NuGet w każdym projekcie testowym .NET w rozwiązaniu.**

Zamiast korzystać z rozszerzeń adaptera testowego, projekty są wymagane do korzystania z pakietów NuGet adaptera testowego. Ten wymóg znacznie poprawia wydajność i powoduje mniejsze problemy związane z ciągłą integracją. Więcej informacji na temat przestarzałych rozszerzeń programu .NET test adapter można znaleźć w [informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli używasz karty testowej nunit 2 i nie można przeprowadzić migracji do karty testowej nunit 3, możesz wyłączyć to nowe zachowanie odnajdywania w programie Visual Studio w wersji 15,8 w **narzędziu**  >  **Opcje**  >  **testów**.

![Zachowanie karty Eksploratora testów w opcjach narzędzi](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Nie znaleziono platformy UWP TestContainer

**Moje testy platformy UWP nie są już wykonywane w programie Visual Studio 2017 w wersji 15,7 lub nowszej.**

Ostatnie projekty testów platformy UWP określają Właściwość Build platformy testowej, która umożliwia lepszą wydajność identyfikowania aplikacji testowych. Jeśli masz projekt testu platformy UWP, który został zainicjowany przed programem Visual Studio w wersji 15,7, ten błąd może pojawić się w  >  **testach** wyjściowych:

**System. AggregateException: wystąpił co najmniej jeden błąd. ---> system. InvalidOperationException: nie znaleziono następującego TestContainer {} w firmie Microsoft. VisualStudio. TestWindow. Controller. TestContainerProvider \<GetTestContainerAsync> D__61. MoveNext ()**

Aby naprawić ten błąd:

- Zaktualizuj Właściwość Build projektu testowego przy użyciu następującego kodu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Zaktualizuj wersję zestawu SDK TestPlatform przy użyciu następującego kodu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Korzystanie z funkcji w wersji zapoznawczej

W programie Visual Studio 2019 możesz dołączać do funkcji w wersji zapoznawczej w obszarze **narzędzia > opcje > środowisku > funkcji w wersji zapoznawczej**.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Korzystanie z flag funkcji

**Jak włączyć flagi funkcji, aby wypróbować nowe funkcje testowania?**

Flagi funkcji są używane do dostarczania eksperymentalnych lub nieukończonych części produktu do Avid użytkowników, którzy chcą przesłać opinię, zanim funkcje zostaną opublikowane oficjalnie. Mogą one spowodować zastabilizację środowiska IDE. Używaj ich tylko w bezpiecznych środowiskach programistycznych, takich jak maszyny wirtualne. Flagi funkcji są zawsze używane na własnych ustawieniach ryzyka. Funkcje eksperymentalne można włączyć za pomocą [rozszerzenia flag funkcji](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)lub w wierszu polecenia dla deweloperów.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagę funkcji za pomocą wiersza polecenia programu Visual Studio Developer, użyj następującego polecenia. Zmień ścieżkę do lokalizacji, w której program Visual Studio jest zainstalowany na komputerze, a następnie Zmień klucz rejestru na żądaną flagę funkcji.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Można wyłączyć flagę z tym samym poleceniem, używając wartości 0 zamiast 1 po DWORD.
::: moniker-end
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](/previous-versions/dd293546(v=vs.110))
- [Testowanie jednostkowe kodu](unit-test-your-code.md)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)