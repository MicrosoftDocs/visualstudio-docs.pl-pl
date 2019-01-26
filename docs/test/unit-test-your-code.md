---
title: Testowanie jednostkowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b490302fe898830afe6ee2c3b8d73ee2454593ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070399"
---
# <a name="unit-test-your-code"></a>Kod testu jednostkowego

Testy jednostkowe pozwalają deweloperom i testerom w szybki sposób sprawdzić występowanie błędów logicznych w metodach klas w projektach C#, Visual Basic i C++.

Narzędzia do testów jednostkowych obejmują:

* **Eksplorator testów**&mdash;można uruchomić testy jednostkowe i wyświetlać ich wyniki w **Eksplorator testów**. Możesz użyć dowolnego środowiska testów jednostkowych, w tym środowiska innych producentów, które posiadają adapter dla **Eksploratora testów**.

* **Środowisko testów jednostkowych Microsoft dla kodu zarządzanego**&mdash;środowiska testów jednostkowych Microsoft dla kodu zarządzanego jest instalowane z Visual Studio i zapewnia platformę do testowania kodu środowiska .NET.

* **Środowisko testów jednostkowych Microsoft dla języka C++**&mdash;środowisko testów jednostkowych Microsoft dla języka C++ jest instalowane jako część **programowanie aplikacji klasycznych w języku C++** obciążenia. Zapewnia platformę do testowania kodu natywnego. Narzędzia CTest, Google Test i Boost.Test platform dostępne są również i karty innej firmy są dostępne dla środowisk testowych dodatkowe. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Narzędzia pokrycia kodu**&mdash;można określić ilość kodu produktu, z jaką bada test jednostkowy jednym poleceniem w Eksploratorze testów.

* **Środowiska izolacji Microsoft Fakes**&mdash;można utworzyć środowiska izolacji substytutów Microsoft zastępcze klasy i metody dla kodu produkcyjnego i systemowego, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

Można również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) aby eksplorować kod .NET w celu wygenerowania danych testu i pakietów testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. W przypadku każdego rozgałęzienia warunkowego w kodzie jest wykonywana analiza przypadku.

## <a name="key-tasks"></a>Główne zadania

Należy skorzystać z następujących tematów, aby lepiej zrozumieć i z łatwością tworzyć testy jednostkowe:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Przewodniki Szybki Start i przewodniki dotyczące:** Użyj poniższych tematów, aby dowiedzieć się, testowanie jednostek w programie Visual Studio z przykładów kodu.|-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Szybki Start: Oparte na testach Programowanie w Eksploratorze testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testowanie jednostek za pomocą narzędzia Eksplorator testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i efektywnych testów jednostkowych.|-   [O teście jednostkowym](../test/unit-test-basics.md)<br />-   [Tworzenie projektu testu jednostkowego](../test/create-a-unit-test-project.md)<br />-   [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)|
|**Testy jednostkowe kodu C++**|-   [Pisanie testów jednostkowych dla języka C/C++ za pomocą Frameworka testów jednostkowych firmy Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Izolowanie testów jednostkowych**|-   [Izolowanie testowanego kodu za pomocą Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Korzystanie z pokrycia kodu do identyfikacji, jaka część kodu projektu jest testowana:** Więcej informacji na temat funkcjonalności pokrycia kodu w narzędzia do testowania programu Visual Studio.|-   [Użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Wykonaj analizy wytrzymałościowej i wydajnościowej przez użycie testów obciążeniowych:** Można utworzyć test obciążenia i dodać testy jednostkowe do niej, aby pomóc wyizolować problemy wytrzymałościowe i wydajnościowe w aplikacji.|-   [Ładowanie testowania (Azure planów testów i TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Ustaw bramki jakości:** Można utworzyć bramki jakości, aby wymusić, że testy są uruchamiane przed kod jest zaewidencjonowany lub scalić, aby zapewnić jakość kodu.|-   [Zasady ewidencjonowania (Azure repozytoriów TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Ustawianie opcji testowania:** Na przykład można określić, gdzie są przechowywane wyniki testu.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Dokumentacja interfejsu API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> w tym artykule opisano przestrzeń nazw UnitTesting, który zawiera atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> w tym artykule opisano przestrzeń unittesting.Web środowiska przestrzeń nazw, która rozszerza przestrzeń nazw UnitTesting przez zapewnienie obsługi dla testów jednostkowych usług sieci web i platformy ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Poprawianie jakości kodu](../test/improve-code-quality.md)
