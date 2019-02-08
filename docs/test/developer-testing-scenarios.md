---
title: Narzędzia do testowania dla deweloperów
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b133a9ce3aa5773349260249ee80edc02d6b318b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954959"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Narzędzia, scenariusze i możliwości testowania dla deweloperów

Obsługa kondycji kodu za pomocą testów jednostkowych. Program Visual Studio oferuje szeroką gamę zaawansowane narzędzia i techniki dla deweloperów do użycia podczas testowania aplikacji.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Unikanie regresji i osiągnięcia pokrycia kodu z funkcją IntelliTest

W tradycyjnych jednostki zestawów testów każdy przypadek testowy reprezentuje scenariusz użycia odszkodowania, a potwierdzenia międzynarodowym relacji między danych wejściowych i wyjściowych.  Weryfikuje, że kilka takich scenariuszy może również być wystarczająca, ale doświadczeni deweloperzy mogą dowiedzieć się błędy znajomą nawet w dobrze przetestowanych kodu, gdy jest to poprawne, ale dane wejściowe lub nieprzetestowanych powodować nieprawidłowe odpowiedzi.

Zasięg i unikanie regresji z funkcją IntelliTest. Funkcja IntelliTest znacznie zmniejsza nakład pracy do tworzenia i obsługi testów jednostkowych dla nowego lub istniejącego kodu.

![Funkcja IntelliTest w działaniu](media/devtest-intellitest.png)

* [Wprowadzenie do funkcji IntelliTest w programie Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest — jeden test, by wszystkimi rządzić](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)
* [Klipy wideo programu IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Rozpoczynanie pracy z funkcją IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Podręcznik dotyczący funkcji IntelliTest](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Interfejs użytkownika, testowanie za pomocą kodowanego interfejsu użytkownika i platformie Selenium

Testowanie interfejsu użytkownika (UI) za pomocą najlepszą na rynku emulatorowi lub społeczności zatwierdzone testowania interfejsu użytkownika. Kodowane testy interfejsu użytkownika umożliwiają tworzenie w pełni zautomatyzowane testy do weryfikowania funkcji i zachowania interfejsu użytkownika aplikacji. Umożliwiają one Automatyzowanie testowania interfejsu użytkownika na różnych technologii, w tym aplikacji opartych na XAML platformy uniwersalnej systemu Windows, aplikacjach przeglądarki i aplikacje programu SharePoint.

Możesz wybrać najlepsze cechy daje kodowanych testów interfejsu użytkownika czy ogólnego oparte na przeglądarce testów interfejsu użytkownika przy użyciu Selenium, Visual Studio udostępnia wszystkie narzędzia, których potrzebujesz.

![Testowanie za pomocą interfejsu użytkownika kodowany interfejs użytkownika](media/devtest-codeduitest.png)

* [Używanie automatyzacji interfejsu użytkownika do testowania kodu](use-ui-automation-to-test-your-code.md)
* [Rozpoczynanie pracy z tworzeniem, edytowaniem i obsługa kodowanego testu interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](test-uwp-app-with-coded-ui-test.md)
* [Testowanie aplikacji programu SharePoint za pomocą kodowanych testów interfejsu użytkownika](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Wprowadzenie do kodowane testy interfejsu użytkownika w programie Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Skuteczne testy jednostkowe w narzędziu pokrycia kodu programu Visual Studio

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny wykonywać lub obejmować dużą część kodu.

Analiza pokrycia kodu mogą dotyczyć zarządzanych i niezarządzanych (natywnych) kod.

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

* [Użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testy jednostkowe, analiza kodu klonowania z programem Visual Studio (Lab) i pokrycia kodu](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Eksplorator testów

**Eksplorator testów** ułatwia deweloperom tworzenie i Uruchamianie testów jednostkowych zarządzanie.

![Visual Studio Test Explorer](media/devtest-testexplorer.png)

* [Wprowadzenie do testów jednostkowych](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Visual Studio jest również extensible i otwiera drzwi biblioteki testowania kart sieciowych, takich jak NUnit i xUnit.net jednostek innej firmy. Ponadto możliwość klonowania kodu przechodzi ręcznie dostępnych w dostarczaniu wysokiej jakości oprogramowania ułatwia identyfikowanie bloki kodu semantycznie podobne, które mogą być kandydatami do wspólnego poprawki lub refaktoryzacji.

![Integracja testowych innych firm](media/devtest-thirdparty.png)

## <a name="see-also"></a>Zobacz także

* [Wprowadzenie do testów jednostkowych](getting-started-with-unit-testing.md)
* [Przyspieszenie wykonywania testów jednostkowych w programie Team Foundation Server](https://blogs.msdn.microsoft.com/devops/2015/07/30/speeding-up-unit-test-execution-in-tfs/)
* [Równoległe i kontekstu wykonania testu jednostki poufne](https://blogs.msdn.microsoft.com/devops/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Testy jednostkowe, analiza kodu klonowania z programem Visual Studio (Lab) i pokrycia kodu](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
