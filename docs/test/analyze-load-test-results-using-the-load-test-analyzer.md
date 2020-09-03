---
title: Analizowanie Wyniki testów obciążenia
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9300dd1ebeaee9d87d2527dbc49fa66e319970c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591245"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia za pomocą analizatora testu obciążenia

Znajdź wąskie gardła, zidentyfikuj błędy i zmierz ulepszenia w aplikacji podczas korzystania z **analizatora testu obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analizuj wyniki testów obciążenia w następujący sposób:

- Monitoruj test obciążenia, gdy jest uruchomiony.

- Analizuj test obciążenia po jego zakończeniu.

- Wyświetl wyniki z poprzedniego testu obciążenia.

Możesz również utworzyć raporty, które porównują dwa lub więcej raportów na potrzeby analizy trendów do udostępnienia uczestnikom projektu. Zobacz [raportowanie wyników testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md).

Te zadania można wykonać, niezależnie od tego, czy test obciążenia ma być uruchamiany z Visual Studio Enterprise, czy z wiersza polecenia, a także od tego, czy test obciążenia ma być uruchamiany na pojedynczym komputerze, czy na komputerze zdalnym.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Różnice między analizowaniem a wykonanym testem obciążenia

Po uruchomieniu testu obciążenia **Analizator testu obciążenia** jest wyświetlany na osobnej karcie, wraz z nazwą testu obciążenia i czasem uruchomienia testu (na przykład **LOADTEST1 [12:40 pm]**). Po uruchomieniu testu obciążenia w pamięci jest zachowywany mniejszy zestaw danych liczników wydajności. Możesz monitorować ten zestaw danych podczas uruchamiania testu obciążenia. Po zakończeniu testu obciążenia można analizować pełny zestaw danych z bazy danych. Istnieją różnice w tym, jakie dane są wyświetlane po uruchomieniu testu obciążenia i jakie dane można zobaczyć po zakończeniu testu obciążenia. Na przykład dane czasu odpowiedzi na 90% i 95 procent nie są obliczane do momentu zakończenia testu obciążenia. Niektóre różnice występują również w funkcjach narzędzi, które są dostępne do analizowania danych.

Po uruchomieniu testu obciążenia dostępne są dwa widoki: widok **wykresy** i widok **tabel** . Widok **wykresy** umożliwia grafowanie liczników wydajności, które są zbierane. Widok **tabele** zawiera informacje o każdym z testów, stron, transakcji i żądań, które są zbierane. Można również wyświetlić tabelę zawierającą błędy.

Domyślnie po zakończeniu przebiegu testu obciążenia jest wyświetlany widok **podsumowania** . Można przełączać się między widokami **Podsumowanie**, **wykresy**, **tabele**i **szczegóły** przy użyciu paska narzędzi. **Analizator testu obciążenia** może być zadokowany lub ustawiony na wartość zmiennoprzecinkową przy użyciu zwykłych technik manipulowania oknem programu Visual Studio. Po przeanalizowaniu ukończonych przebiegów testów obciążenia można jednocześnie otworzyć wiele **analizatorów testów obciążenia** w celu porównania różnych przebiegów testów obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uzyskiwanie dostępu do wyników testu obciążenia:** Po uruchomieniu testu obciążenia z Edytor testu obciążeniowego, wyniki testu obciążenia są otwierane automatycznie, a uruchomiony test obciążenia jest wyświetlany w **analizatorze testu obciążenia**.|-   [Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Dodaj uwagi do analizy do testu obciążenia:** Możesz dodać komentarze do testu obciążenia podczas przeprowadzania analizy. Komentarze są przechowywane na stałe wraz z wynikiem testu obciążenia. Wprowadzony opis jest również wyświetlany w kolumnie **Opis** , która jest skojarzona z testem obciążenia w oknie dialogowym **otwórz i zarządzaj wyniki testów** w Edytor testu obciążeniowego.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: uzyskiwanie dostępu do wyników testów obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ponadto Komentarze są wyświetlane podczas tworzenia raportu programu Excel dla wyników testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md).||
|**Analizowanie wyników testu obciążenia:** Po uzyskaniu dostępu do danych przebiegu testu obciążenia można analizować dane uzyskane. Możesz wyświetlić podsumowanie testu obciążenia, aby szybko zrozumieć wyniki. Podsumowanie testu obciążenia przedstawia klucz w formacie kompaktowym i łatwym do odczytu.<br /><br /> Można wydrukować podsumowanie testu obciążenia. Sprawia to, że jest to wygodne do użycia podczas przekazywania wyników do zainteresowanych stron.<br /><br /> Szczegóły wyników testu obciążenia można analizować za pomocą wykresów i tabel w wynikach. Obejmują one **Błędy**, **strony**, **żądania**, **śledzenie SQL**, **testy**, **progi**i **transakcje**.|-   [Podsumowanie wyników testów obciążenia — Przegląd](../test/load-test-results-summary-overview.md)<br />-   [Instrukcje: wyświetlanie odpowiedzi strony sieci Web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analizowanie aktywności wirtualnego użytkownika w wynikach testu obciążenia, aby wyizolować problemy z wydajnością:** Za pomocą wykresu aktywności wirtualnego użytkownika można wizualizować, co użytkownicy wirtualną wykonuje podczas testu obciążenia. Może to pomóc w odizolowaniu skoków w PROCESORze lub spadku żądań/s oraz określić, które testy lub strony działają podczas tych skoków i odrzuceń.|-   [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
