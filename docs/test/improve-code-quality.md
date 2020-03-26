---
title: Narzędzia do testowania
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 0517d03db180ce76940723ca935be258d0cf1818
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256234"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Pierwsze spojrzenie na narzędzia testowe w programie Visual Studio

Narzędzia do testowania programu Visual Studio mogą pomóc Tobie i Twojemu zespołowi w opracowaniu i utrzymaniu wysokich standardów doskonałości kodu.

> [!NOTE]
> Testowanie jednostkowe jest dostępne we wszystkich wersjach programu Visual Studio. Inne narzędzia testujące, takie jak Live Unit Testing, IntelliTest i Coded UI Test, są dostępne tylko w wersji Visual Studio Enterprise. Aby uzyskać więcej informacji o wersjach, zobacz [Porównanie identyfikatorów programu Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Eksplorator testów

Okno **Eksploratora testów** pomaga deweloperom tworzyć, zarządzać i uruchamiać testy jednostkowe. Można użyć struktury testów jednostkowych firmy Microsoft lub jednej z kilku platform innych firm i open source.

::: moniker range="vs-2017"
![Eksplorator testów programu Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Eksplorator testów programu Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Wprowadzenie do testowania jednostkowego](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Visual Studio jest również rozszerzalny i otwiera drzwi dla innych firm karty testowania jednostek, takich jak NUnit i xUnit.net. Ponadto funkcja klonowania kodu idzie w parze z dostarczaniem wysokiej jakości oprogramowania, pomagając zidentyfikować bloki semantycznie podobnego kodu, które mogą być kandydatami do typowych poprawek błędów lub refaktoryzacji.

![Integracja testowa innych firm](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) automatycznie uruchamia testy jednostkowe w tle i graficznie wyświetla pokrycie kodu i wyniki testów w edytorze kodu programu Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest automatycznie generuje testy jednostkowe i dane testowe dla kodu zarządzanego. IntelliTest zwiększa zasięg i znacznie zmniejsza nakład pracy, aby utworzyć i utrzymać testy jednostkowe dla nowego lub istniejącego kodu.

![IntelliTest w akcji](media/devtest-intellitest.png)

* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest - Jeden test, aby rządzić nimi wszystkimi](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Instrukcja referencyjna IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrycie kodu

[Pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) określa, jaka część kodu projektu jest faktycznie testowana przez kodowane testy, takie jak testy jednostkowe. Aby skutecznie chronić przed błędami, testy powinny wykonywać lub "przykryć" dużą część kodu.

Analiza pokrycia kodu może być stosowana zarówno do kodu zarządzanego, jak i niezarządzanego (natywnego).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

* [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testowanie jednostek, pokrycie kodu i analiza klonów kodu za pomocą programu Visual Studio (Lab)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) pomaga wyizolować testowany kod, zastępując inne części aplikacji skrótami lub podkładkami.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testowanie interfejsu użytkownika za pomocą kodowany interfejs użytkownika i selen

Kodowane testy interfejsu użytkownika umożliwiają tworzenie w pełni zautomatyzowanych testów w celu sprawdzania poprawności funkcjonalności i zachowania interfejsu użytkownika aplikacji. Mogą zautomatyzować testowanie interfejsu użytkownika w różnych technologiach, w tym aplikacjach platformy uniwersalnej systemu Windows opartych na języku XAML, aplikacjach przeglądarki i aplikacjach programu SharePoint.

Niezależnie od tego, czy wybierzesz najlepsze w swojej klasie kodowane testy interfejsu użytkownika, czy ogólne testowanie interfejsu użytkownika oparte na przeglądarce za pomocą selenu, program Visual Studio udostępnia wszystkie narzędzia, których potrzebujesz.

![Testowanie interfejsu użytkownika z kodowanym interfejsem użytkownika](media/devtest-codeduitest.png)

* [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](use-ui-automation-to-test-your-code.md)
* [Wprowadzenie do tworzenia, edytowania i obsługi zakodowanych testów interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](test-uwp-app-with-coded-ui-test.md)
* [Wprowadzenie do zakodowanych testów interfejsu użytkownika w programie Visual Studio Enterprise (Laboratorium)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Testowanie obciążeniowe

[Testowanie obciążenia](../test/quickstart-create-a-load-test-project.md) symuluje obciążenie aplikacji serwera, uruchamiając testy jednostkowe i testy wydajności sieci Web.

## <a name="related-scenarios"></a>Scenariusze pokrewne

* [Badanie & testowanie ręczne (plany testów platformy Azure)](/azure/devops/test/index?view=vsts)
* [Testowanie obciążenia (plany testów platformy Azure)](/azure/devops/test/load-test/index?view=vsts)
* [Ciągłe testowanie (plany testów platformy Azure)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Narzędzia do analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md)
