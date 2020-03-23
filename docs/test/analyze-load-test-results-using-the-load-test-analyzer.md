---
title: Analizowanie wyników testu obciążenia
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591245"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia przy użyciu analizatora testów obciążenia

Znajdowanie wąskich gardeł, identyfikowanie błędów i mierzenie ulepszeń w aplikacji podczas korzystania z **analizatora testów obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analizuj wyniki testów obciążenia w ten sposób:

- Monitoruj test obciążenia, gdy jest uruchomiony.

- Analizowanie testu obciążenia po jego zakończeniu.

- Wyświetlanie wyników poprzedniego testu obciążenia.

Można również utworzyć raporty, które porównują dwa lub więcej raportów do analizy trendów, aby udostępnić je zainteresowanym stronom. Zobacz [Raportowanie wyników testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md).

Można wykonać te zadania, niezależnie od tego, czy test obciążenia zostanie uruchomiony z programu Visual Studio Enterprise, czy z wiersza polecenia, oraz czy test obciążenia jest uruchamiany na jednym komputerze, czy na komputerze zdalnym.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Różnice między analizą uruchomionego i zakończonego testu obciążenia

Po uruchomieniu testu obciążenia **analizator testu obciążenia** jest wyświetlany na osobnej karcie wraz z nazwą testu obciążenia i czasem uruchomienia testu (na przykład **LoadTest1 [12:40 PM]**). Po uruchomieniu testu obciążenia mniejszy zestaw danych licznika wydajności jest obsługiwany w pamięci. Można monitorować ten zestaw danych po uruchomieniu testu obciążenia. Po zakończeniu testu obciążenia można analizować pełny zestaw danych z bazy danych. Istnieją różnice w tym, jakie dane są wyświetlane po uruchomieniu testu obciążenia i jakie dane, które można wyświetlić po zakończeniu testu obciążenia. Na przykład dane czasu odpowiedzi 90 procent i 95 procent nie są obliczane, dopóki test obciążenia nie zostanie zakończony. Niektóre różnice występują również w funkcjonalności narzędzi, które są dostępne do analizy danych.

Po uruchomieniu testu obciążenia dostępne są dwa widoki: widok **Wykresy** i widok **Tabele.** Widok **Wykresy** umożliwia wykres liczników wydajności, które są zbierane. W widoku **Tabele** znajdują się informacje o każdym z testów, stron, transakcji i żądań, które są zbierane. Pojawi się również tabela, która zawiera listę błędów.

Domyślnie po zakończeniu przebiegu testu obciążenia wyświetlany jest widok **Podsumowanie.** Za pomocą paska narzędzi można przełączać się między widokami **Podsumowanie,** **Wykresy,** **Tabele**i **Szczegóły.** **Analizator testu obciążenia** można zadokować lub ustawić, aby float przy użyciu zwykłych technik manipulowania okna programu Visual Studio. Podczas analizowania zakończonych przebiegów testu obciążenia, można mieć wiele **analizatorów testu obciążenia** otwarte w tym samym czasie, aby porównać różne przebiegi testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uzyskiwanie dostępu do wyników testu obciążenia:** Po uruchomieniu testu obciążenia z Edytora testów obciążenia wyniki testu obciążenia otwierają się automatycznie, a test obciążenia bieżącego jest wyświetlany w **analizatorze testów obciążenia**.|-   [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Dodaj uwagi do analizy do testu obciążenia:** Komentarze można dodawać do testu obciążenia podczas przeprowadzania analizy. Komentarze są przechowywane na stałe, wraz z wynikiem testu obciążenia. Wprowadzony opis jest również wyświetlany w kolumnie **Opis** skojarzony z testem obciążenia w oknie dialogowym **Otwieranie i zarządzanie wynikami testów** w Edytorze testów obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ponadto komentarze są wyświetlane podczas tworzenia raportu programu Excel dla wyników testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Raportowanie wyników testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md).||
|**Analiza wyników testu obciążenia:** Po wejściu na dane przebiegu testu obciążenia można analizować wynikowe dane. Można wyświetlić podsumowanie testu obciążenia, aby szybko zrozumieć wyniki. Podsumowanie testu obciążenia pokazuje kluczowe wyniki w kompaktowym i łatwym do odczytania formacie.<br /><br /> Podsumowanie testu obciążenia można wydrukować. Dzięki temu jest wygodny w użyciu podczas przekazywania wyników do zainteresowanych stron.<br /><br /> Można analizować szczegóły wyników testu obciążenia przy użyciu wykresów i tabel w wynikach. Należą do nich **błędy,** **strony,** **żądania,** **śledzenie SQL,** **testy,** **progi**i **transakcje.**|-   [Podsumowanie wyników testu obciążenia](../test/load-test-results-summary-overview.md)<br />-   [Jak: Wyświetlanie odpowiedzi na stronę internetową](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizowanie wyników testu obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analizowanie aktywności użytkownika wirtualnego w wynikach testu obciążenia w celu wyizolowania problemów z wydajnością:** Za pomocą wykresu aktywności użytkownika wirtualnego można wizualizować, co użytkownicy wirtualni robią podczas testu obciążenia. Może to pomóc wyizolować skoki w procesorze CPU lub spadki żądań/s i określić, które testy lub strony są uruchomione podczas tych skoków i upadków.|-   [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
