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
ms.openlocfilehash: 153624ec6f0bdb13e4d89a92edf977d0badc7e62
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712218"
---
# <a name="testing-tools-in-visual-studio"></a>Narzędzia do testowania w programie Visual Studio

Program Visual Studio, narzędzia do testowania pomaga i zespołowi opracowywać i utrzymywać wysokie standardy doskonałości kodu.

> [!NOTE]
> Testy jednostkowe jest dostępna we wszystkich wersjach programu Visual Studio. Inne narzędzia do testowania, takie jak Live Unit Testing, IntelliTest i kodowany test interfejsu użytkownika, są dostępne tylko w wersji Visual Studio Enterprise. Aby uzyskać więcej informacji na temat wersji, zobacz [porównanie programu Visual Studio środowisk IDE](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Eksplorator testów

Okno **Eksplorator testów** ułatwia deweloperom tworzenie i uruchamianie testów jednostkowych oraz zarządzanie nimi. Można użyć frameworka testów jednostkowych firmy Microsoft lub jednego z kilku struktur innych firm i open source.

::: moniker range="vs-2017"
![Visual Studio Test Explorer](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio Test Explorer 16,2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Wprowadzenie do testów jednostkowych](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Program Visual Studio jest również rozszerzalny i otwiera drzwi dla kart testów jednostkowych innych firm, takich jak NUnit i xUnit.net. Ponadto funkcja klonowania kodu prowadzi do pracy z dostarczaniem wysokiej jakości oprogramowania, ułatwiając identyfikację bloków podobnego kodu, który może być kandydatami do typowych poprawek lub refaktoryzacji błędów.

![Integracja testów innych firm](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) automatycznie uruchamia testy jednostkowe w tle i wyświetla w postaci graficznej wyniki pokrycia i testowanie kodu w edytorze kodu programu Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest automatycznie generuje testy jednostkowe i dane testowe dla kodu zarządzanego. IntelliTest poprawia pokrycie i znacząco zmniejsza nakłady na tworzenie i konserwowanie testów jednostkowych w nowym lub istniejącym kodzie.

![IntelliTest w działaniu](media/devtest-intellitest.png)

* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — jeden test do reguły dla nich](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Podręcznik dotyczący funkcji IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrycie kodu

[Pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) Określa, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe. Aby skutecznie zabezpieczyć się przed błędami, testy powinny być wykonywane lub "pokrywające" znaczną część kodu.

Analiza pokrycia kodu może być stosowana do kodu zarządzanego i niezarządzanego (natywnego).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

* [Użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testowanie jednostkowe, pokrycie kodu i analiza klonowania kodu za pomocą programu Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

Sztuczne [firmy Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) ułatwiają odizolowanie testowanego kodu przez zastąpienie innych części aplikacji za pomocą wycinków lub podkładek.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testowanie interfejsu użytkownika przy użyciu kodowanego interfejsu użytkownika i selenu

Kodowane testy interfejsu użytkownika umożliwiają tworzenie w pełni zautomatyzowanych testów w celu zweryfikowania funkcjonalności i zachowania interfejsu użytkownika aplikacji. Mogą automatyzować testy interfejsu użytkownika w różnych technologiach, w tym aplikacji platformy UWP opartych na języku XAML, aplikacjach przeglądarki i aplikacji programu SharePoint.

Bez względu na to, czy wybierasz najlepsze, kodowane testy interfejsu użytkownika, czy ogólne testy interfejsu użytkownika oparte na przeglądarce przy użyciu selenu, program Visual Studio udostępnia wszystkie potrzebne narzędzia.

![Testowanie interfejsu użytkownika za pomocą kodowanego interfejsu użytkownika](media/devtest-codeduitest.png)

* [Używanie automatyzacji interfejsu użytkownika do testowania kodu](use-ui-automation-to-test-your-code.md)
* [Wprowadzenie do tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testowanie aplikacji platformy UWP przy użyciu kodowanych testów interfejsu użytkownika](test-uwp-app-with-coded-ui-test.md)
* [Wprowadzenie do kodowanych testów interfejsu użytkownika za pomocą Visual Studio Enterprise (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Testowanie obciążenia

[Testowanie obciążeniowe](../test/quickstart-create-a-load-test-project.md) symuluje obciążenie aplikacji serwera, uruchamiając testy jednostkowe i testy wydajności sieci web.

## <a name="related-scenarios"></a>Scenariusze pokrewne

* [Poznawcze i ręczne testowanie (planów testowych platformy Azure)](/azure/devops/test/index?view=vsts)
* [Ładowanie testów (planów testowych platformy Azure)](/azure/devops/test/load-test/index?view=vsts)
* [Ciągłe testowanie (planów testowych platformy Azure)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Narzędzia do analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md)
