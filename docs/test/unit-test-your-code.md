---
title: Testowanie jednostkowe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ffe383d2195feb6689954a8ec858b196bae8c06a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565997"
---
# <a name="unit-test-your-code"></a>Jednostka przetestować swój kod

Testy jednostkowe dają deweloperom i testerom szybki sposób wyszukiwania błędów logicznych w metodach klas w projektach C#, Visual Basic i C++.

Narzędzia do testów jednostkowych obejmują:

* **Uruchom eksploratora**&mdash;testów jednostkowych i zobacz ich wyniki w **Eksploratorze testów**. Można użyć dowolnej struktury testów jednostkowych, w tym struktury innej firmy, która ma kartę dla **Eksploratora testów.**

* **Struktura testów jednostkowych firmy Microsoft dla kodu**&mdash;zarządzanego Struktura testu jednostkowego firmy Microsoft dla kodu zarządzanego jest zainstalowana w programie Visual Studio i zapewnia platformę do testowania kodu .NET.

* **Struktura testów jednostkowych firmy Microsoft dla języka C++**&mdash;Struktura testów jednostkowych firmy Microsoft dla języka C++ jest instalowana jako część programu Desktop development z obciążeniem **języka C++.** Zapewnia platformę do testowania kodu macierzystego. Google Test, Boost.Test i CTest struktury są również uwzględnione, a karty innych firm są dostępne dla dodatkowych struktur testowych. Aby uzyskać więcej informacji, zobacz [Pisanie testów jednostkowych dla języka C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Narzędzia pokrycia kodu**&mdash;Można określić ilość kodu produktu, który testy jednostkowe wykonywania z jednego polecenia w Eksploratorze testów.

* **Microsoft Fakes izolacji framework**&mdash;Microsoft Fakes izolacji framework można utworzyć klasy zastępcze i metody dla produkcji i kodu systemu, które tworzą zależności w kodzie w ramach testu. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

[IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) można również użyć do eksplorowania kodu .NET do generowania danych testowych i zestawu testów jednostkowych. Dla każdej instrukcji w kodzie jest generowany test danych wejściowych, który wykona tę instrukcję. Analiza przypadków jest wykonywana dla każdej gałęzi warunkowej w kodzie.

## <a name="key-tasks"></a>Główne zadania

Użyj następujących artykułów, aby ułatwić zrozumienie i tworzenie testów jednostkowych:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Szybkie starty i wskazówki:** Dowiedz się więcej o testowaniu jednostkowym w programie Visual Studio na podstawie przykładów kodu.|- [Instruktaż: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Szybki start: program rozwoju opartego na testach za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Jak: Dodawanie testów jednostkowych do aplikacji języka C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testowanie jednostkowe za pomocą Eksploratora testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i wydajnych testów jednostkowych.|- [Podstawy testu jednostkowego](../test/unit-test-basics.md)<br />- [Tworzenie projektu testu jednostkowego](../test/create-a-unit-test-project.md)<br />- [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalowanie struktur testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)|
|**Kod C++ testu jednostkowego**|- [Zapis testów jednostkowych dla języka C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Testy jednostkowe izolujące**|- [Izolowanie kodu w trakcie testu za pomocą Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Użyj pokrycia kodu, aby określić, jaka część kodu projektu jest testowana:** Dowiedz się więcej o funkcji pokrycia kodu narzędzi do testowania programu Visual Studio.|- [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Przeprowadzaj analizę naprężeń i wydajności przy użyciu testów obciążenia:** Dowiedz się, jak tworzyć testy obciążenia, aby ułatwić wyizolowanie problemów z wydajnością i stresem w aplikacji.|- [Szybki start: tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md)<br />- [Testowanie obciążenia (plany testów platformy Azure i TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Ustaw bramy jakościowe:** Dowiedz się, jak utworzyć bramy jakości, aby wymusić, że testy są uruchamiane przed zaewidencjonowania lub scalenia kodu.|- [Zasady ewidencjonowania (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Ustaw opcje testowania:** Dowiedz się, jak skonfigurować opcje testów, na przykład, gdzie są przechowywane wyniki testów.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Dokumentacja referencyjna interfejsu API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>opisuje UnitTesting przestrzeni nazw, która zawiera atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testowanie jednostek.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>opisuje unittesting.web przestrzeni nazw, która rozszerza obszar nazw UnitTesting, zapewniając obsługę ASP.NET i testów jednostek usługi sieci web.

## <a name="see-also"></a>Zobacz też

- [Poprawa jakości kodu](../test/improve-code-quality.md)
