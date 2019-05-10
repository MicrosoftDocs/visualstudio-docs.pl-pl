---
title: Narzędzia do testowania
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 435eb2571f709f3ed5df4effbfdf3b5f4970457b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461393"
---
# <a name="testing-tools-in-visual-studio"></a>Narzędzia do testowania w programie Visual Studio

Program Visual Studio, narzędzia do testowania pomaga i zespołowi opracowywać i utrzymywać wysokie standardy doskonałości kodu.

> [!NOTE]
> Testy jednostkowe jest dostępna we wszystkich wersjach programu Visual Studio. Inne narzędzia testowania, takie jak Live Unit Testing, IntelliTest i kodowanego testu interfejsu użytkownika są dostępne tylko w programie Visual Studio Enterprise. Aby uzyskać więcej informacji dotyczących wersji zobacz [porównanie środowiska IDE programu Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** okna ułatwia deweloperom tworzenie i Uruchamianie testów jednostkowych zarządzanie. Można użyć frameworka testów jednostkowych firmy Microsoft lub jednego z kilku struktur innych firm i open source.

![Visual Studio Test Explorer](media/devtest-testexplorer.png)

* [Wprowadzenie do testów jednostkowych](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Visual Studio jest również extensible i otwiera drzwi biblioteki testowania kart sieciowych, takich jak NUnit i xUnit.net jednostek innej firmy. Ponadto możliwość klonowania kodu przechodzi ręcznie dostępnych w dostarczaniu wysokiej jakości oprogramowania ułatwia identyfikowanie bloki kodu semantycznie podobne, które mogą być kandydatami do wspólnego poprawki lub refaktoryzacji.

![Integracja testowych innych firm](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) automatycznie uruchamia testy jednostkowe w tle i wyświetla w postaci graficznej wyniki pokrycia i testowanie kodu w edytorze kodu programu Visual Studio.

## <a name="intellitest"></a>IntelliTest

Funkcja IntelliTest automatycznie generuje testy jednostkowe i dane z badań dla kodu zarządzanego. Funkcja IntelliTest zwiększa pokrycia i znacznie zmniejsza nakład pracy do tworzenia i obsługi testów jednostkowych dla nowego lub istniejącego kodu.

![Funkcja IntelliTest w działaniu](media/devtest-intellitest.png)

* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — jeden test, by wszystkimi rządzić](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Podręcznik dotyczący funkcji IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrycie kodu

[Pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) Określa, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe. Aby skutecznie zabezpieczyć się przed błędami, testy powinny wykonywać lub "cover" znaczną część kodu.

Analiza pokrycia kodu mogą dotyczyć zarządzanych i niezarządzanych (natywnych) kod.

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

* [Użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testy jednostkowe, analiza kodu klonowania z programem Visual Studio (Lab) i pokrycia kodu](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) pomaga w izolowaniu kodu, które testujesz przez zastąpienie innych części aplikacji wycinków i podkładek.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Interfejs użytkownika, testowanie za pomocą kodowanego interfejsu użytkownika i platformie Selenium

Kodowane testy interfejsu użytkownika umożliwiają tworzenie w pełni zautomatyzowane testy do weryfikowania funkcji i zachowania interfejsu użytkownika aplikacji. Umożliwiają one Automatyzowanie testowania interfejsu użytkownika na różnych technologii, w tym aplikacji opartych na XAML platformy uniwersalnej systemu Windows, aplikacjach przeglądarki i aplikacje programu SharePoint.

Czy możesz wybrać najlepszy branży kodowanych testów interfejsu użytkownika lub ogólny oparte na przeglądarce testów interfejsu użytkownika przy użyciu Selenium, program Visual Studio udostępnia wszystkie narzędzia, których potrzebujesz.

![Testowanie za pomocą interfejsu użytkownika kodowany interfejs użytkownika](media/devtest-codeduitest.png)

* [Używanie automatyzacji interfejsu użytkownika do testowania kodu](use-ui-automation-to-test-your-code.md)
* [Rozpoczynanie pracy z tworzeniem, edytowaniem i obsługa kodowanego testu interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](test-uwp-app-with-coded-ui-test.md)
* [Wprowadzenie do kodowane testy interfejsu użytkownika w programie Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Testowanie obciążenia

[Testowanie obciążeniowe](../test/quickstart-create-a-load-test-project.md) symuluje obciążenie aplikacji serwera, uruchamiając testy jednostkowe i testy wydajności sieci web.

## <a name="related-scenarios"></a>Scenariusze pokrewne

* [Poznawcze i ręczne testowanie (planów testowych platformy Azure)](/azure/devops/test/index?view=vsts)
* [Ładowanie testów (planów testowych platformy Azure)](/azure/devops/test/load-test/index?view=vsts)
* [Ciągłe testowanie (planów testowych platformy Azure)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Narzędzia do analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md)
