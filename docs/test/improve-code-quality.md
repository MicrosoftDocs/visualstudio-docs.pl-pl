---
title: Narzędzia do testowania
description: Dowiedz się Visual Studio narzędzia do testowania kodu mogą pomóc Ci i Twoje zespołowi opracować i utrzymać wysokie standardy doskonałości kodu.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e2224ffc1776a15453d1382872c2d3f5a9e86c3c
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760955"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Najpierw przyjrzyj się narzędziom do testowania w Visual Studio

Narzędzia do testowania w programie Visual Studio mogą ułatwić Tobie i Twojemu zespołowi tworzenie i utrzymywanie wysokich standardów jakości kodu.

> [!NOTE]
> Testy jednostkowe są dostępne we wszystkich wersjach Visual Studio. Inne narzędzia do testowania, takie jak Live Unit Testing i IntelliTest, są dostępne tylko w Visual Studio Enterprise wersji. Aby uzyskać więcej informacji na temat wersji, zobacz [Porównanie Visual Studio IE.](https://visualstudio.microsoft.com/vs/compare/)

## <a name="test-explorer"></a>Eksplorator testów

Okno **Eksplorator testów** ułatwia deweloperom tworzenie i uruchamianie testów jednostkowych oraz zarządzanie nimi. Możesz użyć struktury testów jednostkowych firmy Microsoft lub jednej z kilku platform testów open source innych firm.

::: moniker range="vs-2017"
![Visual Studio Eksploratora testów](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range=">=vs-2019"
![Visual Studio Eksploratora testów 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Rozpoczynanie pracy z testami jednostkowymi](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Visual Studio jest również rozszerzalny i otwiera drzwi dla adapterów testów jednostkowych innych firm, takich jak NUnit i xUnit.net. Ponadto możliwość klonowania kodu umożliwia dostarczanie oprogramowania wysokiej jakości, pomagając w identyfikowaniu bloków kodu podobnego semantycznie, które mogą być kandydatami do typowych poprawek błędów lub refaktoryzacji.

![Integracja testów innych firm](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) automatycznie uruchamia testy jednostkowe w tle, a następnie wyświetla graficznie pokrycie kodu i wyniki testów w Visual Studio kodu.

> [!NOTE]
> Testy jednostkowe na żywo są dostępne tylko w wersji Enterprise i są obsługiwane tylko w przypadku kodu .NET.

## <a name="intellitest"></a>IntelliTest

Funkcja IntelliTest automatycznie generuje testy jednostkowe i dane testowe dla kodu zarządzanego. Funkcja IntelliTest zwiększa pokrycie i znacznie zmniejsza nakład pracy na tworzenie i konserwację testów jednostkowych dla nowego lub istniejącego kodu.

![IntelliTest w działaniu](media/devtest-intellitest.png)

> [!NOTE]
> Funkcja IntelliTest jest dostępna tylko w wersji Enterprise. Jest on obsługiwany w przypadku kodu C#, który jest przeznaczony dla .NET Framework. Program .NET Core .NET Standard nie jest obecnie obsługiwany.

* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — jeden test, który ma wszystkie reguły](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Podręcznik referencyjny funkcji IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrycie kodu

[Pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) określa, jaka część kodu projektu jest faktycznie testowana przez kodowane testy, takie jak testy jednostkowe. Aby skutecznie chronić się przed błędami, testy powinny "obejmować" znaczną część kodu.

> [!NOTE]
> Pokrycie kodu jest dostępne tylko w wersji Enterprise.

Analizę pokrycia kodu można zastosować zarówno do kodu zarządzanego, jak i nieza zarządzania (natywnego).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

* [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testowanie jednostkowe, pokrycie kodu i analiza klonowania kodu Visual Studio (laboratorium)](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) odizolować testowany kod, zastępując inne części aplikacji wycinkami lub podkładkami.

> [!NOTE]
> Microsoft Fakes są dostępne tylko w wersji Enterprise i są obsługiwane tylko w przypadku kodu .NET.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testowanie interfejsu użytkownika za pomocą kodego interfejsu użytkownika i Selenium

Kodowane testy interfejsu użytkownika zapewniają sposób tworzenia w pełni zautomatyzowanych testów w celu zweryfikowania funkcjonalności i zachowania interfejsu użytkownika aplikacji. Mogą one automatyzować testowanie interfejsu użytkownika za pomocą różnych technologii, w tym aplikacji platformy UWP opartych na języku XAML, aplikacji przeglądarki i aplikacji SharePoint.

> [!NOTE]
> Kodowany interfejs użytkownika to przestarzała funkcja.

Niezależnie od tego, czy wybierasz najlepsze kodowane testy interfejsu użytkownika, czy ogólne testy interfejsu użytkownika oparte na przeglądarce przy użyciu selenium, Visual Studio udostępnia wszystkie potrzebne narzędzia.

![Testowanie interfejsu użytkownika za pomocą kodowego interfejsu użytkownika](media/devtest-codeduitest.png)

* [Testowanie kodu przy użyciu automatyzacji interfejsu użytkownika](use-ui-automation-to-test-your-code.md)
* [Wprowadzenie do tworzenia, edytowania i obsługi kodowego testu interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testowanie aplikacji platformy UWP za pomocą kodowych testów interfejsu użytkownika](test-uwp-app-with-coded-ui-test.md)
* [Wprowadzenie do kodowych testów interfejsu użytkownika za Visual Studio Enterprise (laboratorium)](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>Scenariusze pokrewne

* [Testowanie eksploracyjne & ręczne (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Testowanie obciążenia (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Testowanie ciągłe (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Narzędzia do analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md)
