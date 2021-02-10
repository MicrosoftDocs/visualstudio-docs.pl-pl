---
title: Narzędzia testów jednostkowych & zadania
description: Dowiedz się więcej o narzędziach testów jednostkowych, których można użyć w celu zapewnienia deweloperom i testerom szybkiego sposobu wyszukiwania błędów logiki w kodzie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 718f5560176f287f237d54a89bd44c831c7f03ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962616"
---
# <a name="unit-test-tools-and-tasks"></a>Narzędzia i zadania dla testów jednostkowych

Testy jednostkowe umożliwiają deweloperom i testerom szybkie wyszukiwanie błędów logicznych w metodach klas w projektach C#, Visual Basic i C++.

Narzędzia do testów jednostkowych obejmują:

* **Eksplorator testów** &mdash; Uruchom testy jednostkowe i zobacz ich wyniki w **Eksploratorze testów**. Można użyć dowolnego środowiska testów jednostkowych, w tym struktury innej firmy, która ma adapter dla **Eksploratora testów**.

* **Środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego** &mdash; Środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu platformy .NET.

* **Środowisko testów jednostkowych firmy Microsoft dla języka C++** &mdash; Środowisko testów jednostkowych firmy Microsoft dla języka C++ jest instalowane w ramach **programowania aplikacji klasycznych w języku c++** . Zapewnia ona platformę do testowania kodu natywnego. Dostępne są również Google Test, usprawnienia i struktury narzędzia ctest, a także karty innych firm dla dodatkowych platform testowych. Aby uzyskać więcej informacji, zobacz [pisać testy jednostkowe dla C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Narzędzia** &mdash; pokrycia kodu Można określić ilość kodu produktu, który test jednostkowy wykonuje z jednego polecenia w Eksploratorze testów.

* Struktura izolacji elementów sztucznych **firmy Microsoft** &mdash; Środowisko izolacji sztucznej firmy Microsoft może tworzyć zastępcze klasy i metody dla kodu środowiska produkcyjnego i systemu .NET, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

W przypadku platformy .NET można także użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) do eksplorowania kodu i generowania danych testowych oraz zestawu testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, które spowodują wykonanie tej instrukcji. Analiza przypadku jest wykonywana dla każdego rozgałęzienia warunkowego w kodzie.

## <a name="key-tasks"></a>Główne zadania

Skorzystaj z poniższych artykułów, aby zrozumieć i utworzyć testy jednostkowe:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Przewodniki Szybki Start i wskazówki:** Poznaj testy jednostkowe w programie Visual Studio z przykładów kodu.|- [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu platformy .NET](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Przewodnik: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Instrukcje: Dodawanie testów jednostkowych do aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testy jednostkowe w Eksploratorze testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i wydajnych testów jednostkowych.|- [Podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md)<br />- [Tworzenie projektu testu jednostkowego](../test/create-a-unit-test-project.md)<br />- [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)|
|**Test jednostkowy kodu C++**|- [Zapisz testy jednostkowe dla C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Użyj pokrycia kodu, aby określić, jaka część kodu projektu jest testowana:** Dowiedz się więcej o funkcji pokrycia kodu narzędzi testowych programu Visual Studio.|- [Użyj pokrycia kodu, aby określić, jaka część kodu jest testowana](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Izolowanie testów jednostkowych**|- [Izolowanie testowanego kodu platformy .NET przy użyciu elementów sztucznych firmy Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Wykonaj analizę obciążeniową i wydajnością, używając testów obciążeniowych:** Dowiedz się, jak tworzyć testy obciążeniowe, aby ułatwić odizolowanie problemów z wydajnością i obciążeniem w aplikacji (przestarzałe).|- [Szybki Start: Tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md)<br />- [Testowanie obciążenia (Azure Test Plans i TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Ustawianie bram jakości:** Dowiedz się, jak utworzyć bramy jakości, aby wymusić, że testy są uruchamiane przed zaewidencjonowaćm lub scaleniem kodu.|- [Zasady ewidencjonowania (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Ustawianie opcji testowania:** Dowiedz się, jak skonfigurować opcje testu, na przykład, gdzie są przechowywane wyniki testów.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Dokumentacja referencyjna interfejsu API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Opisuje przestrzeń nazw UnitTesting, która udostępnia atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> Opisuje przestrzeń nazw UnitTesting. Web, która rozszerza przestrzeń nazw UnitTesting przez zapewnienie wsparcia dla ASP.NET i testów jednostkowych usług sieci Web.

## <a name="see-also"></a>Zobacz też

- [Poprawianie jakości kodu](../test/improve-code-quality.md)