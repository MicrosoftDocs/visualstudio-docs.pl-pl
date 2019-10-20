---
title: Testowanie jednostkowe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: fd6d6dca2680dcfcaa42912333b080c428ba78d2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659847"
---
# <a name="unit-test-your-code"></a>Testowanie jednostkowe kodu

Testy jednostkowe umożliwiają deweloperom i testerom szybkie wyszukiwanie błędów logicznych w metodach klas w C#, Visual Basic i C++ projektach.

Narzędzia do testów jednostkowych obejmują:

* **Eksplorator testów** &mdash;Run testy jednostkowe i Zobacz wyniki w **Eksploratorze testów**. Można użyć dowolnego środowiska testów jednostkowych, w tym struktury innej firmy, która ma adapter dla **Eksploratora testów**.

* **Środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego** &mdash;The Framework testów jednostkowych firmy Microsoft dla kodu zarządzanego jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu platformy .NET.

* **Środowisko testów jednostkowych firmy C++ Microsoft dla** &mdash;The Framework testów jednostkowych Microsoft dla C++ programu jest instalowane w ramach **opracowywania aplikacji C++ klasycznych** . Zapewnia ona platformę do testowania kodu natywnego. Dostępne są również Google Test, usprawnienia i struktury narzędzia ctest, a także karty innych firm dla dodatkowych platform testowych. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dlaC++języka C/](../test/writing-unit-tests-for-c-cpp.md).

* **Narzędzia pokrycia kodu** &mdash;You mogą określić ilość kodu produktu, który test jednostkowy wykonuje z jednego polecenia w Eksploratorze testów.

* **Struktura izolacji sztucznej firmy microsoft** &mdash;The struktura izolacji firmy Microsoft sztuczna może tworzyć zastępcze klasy i metody dla kodu produkcyjnego i systemowego, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

Możesz również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) do eksplorowania kodu .NET, aby generować dane testowe i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, które spowodują wykonanie tej instrukcji. Analiza przypadku jest wykonywana dla każdego rozgałęzienia warunkowego w kodzie.

## <a name="key-tasks"></a>Główne zadania

Skorzystaj z poniższych artykułów, aby zrozumieć i utworzyć testy jednostkowe:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Przewodniki Szybki Start i wskazówki:** Poznaj testy jednostkowe w programie Visual Studio z przykładów kodu.|[przewodnik - : Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [: Dodawanie testów jednostkowych do C++ aplikacji](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testy jednostkowe w Eksploratorze testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i wydajnych testów jednostkowych.|[podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md) - <br />- [utworzyć projekt testu jednostkowego](../test/create-a-unit-test-project.md)<br />- [uruchomić testy jednostkowe za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md)<br />- [zainstalować platformy testów jednostkowych](../test/install-third-party-unit-test-frameworks.md) innych firm|
|**Kod testu C++ jednostkowego**|- [pisać testy jednostkowe dla CC++ /](../test/writing-unit-tests-for-c-cpp.md)|
|**Izolowanie testów jednostkowych**|- [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md) elementów sztucznych firmy Microsoft|
|**Użyj pokrycia kodu, aby określić, jaka część kodu projektu jest testowana:** Dowiedz się więcej o funkcji pokrycia kodu narzędzi testowych programu Visual Studio.|- [użyć pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Wykonaj analizę obciążeniową i wydajnością, używając testów obciążeniowych:** Dowiedz się, jak tworzyć testy obciążeniowe, aby ułatwić odizolowanie problemów z wydajnością i obciążeniem w aplikacji.|- [Szybki Start: Tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md)<br />- [testowanie obciążenia (Azure test Plans i TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Ustawianie bram jakości:** Dowiedz się, jak utworzyć bramy jakości, aby wymusić, że testy są uruchamiane przed zaewidencjonowaćm lub scaleniem kodu.|[zasady ewidencjonowania -  (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Ustawianie opcji testowania:** Dowiedz się, jak skonfigurować opcje testu, na przykład, gdzie są przechowywane wyniki testów.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Dokumentacja interfejsu API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> opisuje przestrzeń nazw UnitTesting, która udostępnia atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> opisuje przestrzeń nazw UnitTesting. Web, która rozszerza przestrzeń nazw UnitTesting przez zapewnienie wsparcia dla ASP.NET i testów jednostkowych usług sieci Web.

## <a name="see-also"></a>Zobacz także

- [Poprawianie jakości kodu](../test/improve-code-quality.md)
