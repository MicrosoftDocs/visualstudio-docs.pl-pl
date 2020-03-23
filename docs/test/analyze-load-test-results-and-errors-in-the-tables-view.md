---
title: Analizowanie wyników i błędów testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e337c30a4b6a08f123ef7ee33dee704e9412de
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565178"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizowanie wyników i błędów testów obciążenia w widoku Tabele analizatora testów obciążenia

Podczas wyświetlania wyników przebiegu testu obciążenia można wyświetlić różne okienka, które zapewniają różne sposoby analizowania danych. Można wyświetlić dane jako wykres, aby zobaczyć, jak zmienia się wraz z czasem, lub można wyświetlić dane jako szczegółowe tabele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby przełączyć się do widoku tabeli, wybierz pozycję **Tabele** na pasku narzędzi **testu obciążenia.** Aby przełączać się między różnymi tabelami, użyj listy rozwijanej **Tabela** na pasku narzędzi nad siatką tabeli. W widoku tabeli można wyświetlać maksymalnie cztery tabele naraz. Aby uzyskać więcej informacji, zobacz [tabele testów obciążenia kafelków](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) w tym temacie.

Większość wartości liczbowych wyświetlanych w tabeli dla liczników wydajności kumuluje się w całym przebiegu testu obciążenia. Kolumny o nazwie **Last** są wyjątkiem i reprezentują wartość z ostatniego interwału próbkowania.

> [!NOTE]
> Kolumny o nazwie **Last** są dostępne tylko podczas wykonywania testu obciążenia. Po zakończeniu testu obciążenia te kolumny nie są dostępne.

Większość tabel można sortować, wybierając tytuł kolumny, którą chcesz posortować. Domyślnie w niektórych tabelach nie są wyświetlane wszystkie dostępne kolumny. Kolumny można dodawać do tabel, jeśli kolumny są dostępne. Aby dodać kolumny, kliknij ją prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj/Usuń kolumny**.

> [!NOTE]
> Dane z tabeli można skopiować do innych aplikacji, takich jak Excel, w celu dodatkowej analizy.

## <a name="the-load-test-tables"></a>Tabele testów obciążenia

W poniższej tabeli wymieniono tabele, które są dostępne do analizowania przebiegów testów obciążenia.

|Nazwa tabeli|Opis|
|-|-|
|Errors|Wyświetla listę błędów, które wystąpiły podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [tabela Błędy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) w tym temacie i [Analizuj wyniki testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Strony|Wyświetla listę stron dostępnych podczas przebiegu testu obciążenia. Niektóre dane w tej tabeli są dostępne tylko po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie odpowiedzi na stronę internetową](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Żądania|Wyświetla szczegóły dla poszczególnych żądań wystawionych podczas testu obciążenia. Obejmuje to wszystkie żądania HTTP i żądania zależne, takie jak obrazy. Aby uzyskać więcej informacji, zobacz [żądania tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) w tym temacie.|
|Śledzenie SQL|Wyświetla wyniki śledzenia SQL. Ta tabela jest dostępna tylko po zakończeniu testu obciążenia i tylko wtedy, gdy podczas testu użyto śledzenia SQL. Aby uzyskać więcej informacji, zobacz [tabelę danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) w tym temacie.|
|Testy|Wyświetla szczegóły dla poszczególnych testów uruchamianych podczas testu obciążenia. Aby uzyskać więcej informacji, zobacz [tabeli testy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) w tym temacie.|
|Progi|Wyświetla listę naruszeń reguły progowej, które wystąpiły podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakcje|Wyświetla listę transakcji, które wystąpiły podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Tabela Transakcje](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) w tym temacie.|
|Agenci|Wyświetla się tylko wtedy, gdy test obciążenia używa kontrolera testów i agentów testowych. Wyświetla listę agentów, które były używane podczas przebiegu testu obciążenia. Tabela Agenci zawiera ile żądań testowany agent i tych żądań, ile nie powiodło się. Ponadto agentów tabeli zawiera liczbę testów w testach obciążenia mix, że agent testowany i tych, ile nie powiodło się.|
|Szczegóły testu|Wyświetla szczegóły dotyczące testów zawartych w zestawieniu testów dla testu obciążenia. Szczegóły obejmują nazwę testu, scenariusz, w którym test był, czas, w którym rozpoczął się test, czas, przez jaki test trwał do uruchomienia, oraz wynik testu wskazujący, czy test przebiegł niepowodzeniem lub nie powiódł się. Jeśli test nie powiódł się, łącze jest obecne w **kolumnie Szczegóły.** Można wybrać łącze, które spowoduje, że przejdziesz do Edytora testów wydajności sieci Web z wyróżnionym żądaniem, które nie powiodło się.|

## <a name="collect-percentile-data"></a>Zbieranie danych percentyla

Niektóre tabele testów obciążenia mogą zawierać dodatkowe kolumny, które zawierają dane percentylu i czasy odpowiedzi podzielone na grupy na podstawie emulacji sieci. Domyślnie te dane nie są zbierane. Dane percentyla są dostępne tylko wtedy, gdy wyniki są zapisywane w bazie danych, a nie podczas zapisywania lokalnego. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ponadto, aby zebrać te dane, w **Edytorze testów obciążenia**, w węźle **Uruchom ustawienia,** wybierz węzeł ustawienia określonego uruchomienia, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz opcję **StatisticsOnly** lub **AllIndividualDetails**. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie odpowiedzi na stronę internetową](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabela Żądania

W tabeli **Żądania** są wyświetlane szczegółowe informacje dotyczące poszczególnych żądań wystawionych podczas testu obciążenia. Obejmuje to wszystkie żądania HTTP i żądania zależne, takie jak obrazy. Tabela zawiera listę żądań według testów i scenariuszy, ponieważ jedno żądanie może zostać uwzględnione w wielu testach i scenariuszach.

W poniższej tabeli wymieniono kolumny w tabeli **Żądania:**

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|**Żądanie**|Adres URL żądania. Na przykład *home.html*lub *orange-arrow.gif*.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łącznie**|Całkowita liczba tego żądania testu wydajności sieci web wydane podczas przebiegu testu obciążenia. Suma obejmuje przekazane i nieudane żądania, ale nie obejmuje żądań buforowanych, ponieważ nie są one wystawiane na serwerze sieci web.|Tak|
|**Przekazywane**|Ile razy żądanie zostało wydane i przekazane.|Nie|
|**Niepowodzenie**|Liczba wyświetlonych i nie powiodła się liczba wyświetlonych żądania. Wpisy w tej kolumnie są wyświetlane jako hiperłącza. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów w oknie dialogowym **Błędy testu obciążenia.** Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Buforowane**|Całkowita liczba buforowanych żądań.|Nie|
|**Żądania/s**|Szybkość na sekundę żądania podczas przebiegu testu obciążenia.|Nie|
|**Przekazany/s**|Stawka na sekundę tego żądania podczas przebiegu testu obciążenia dla wystąpień tego żądania, które przeszły.|Nie|
|**Nie powiodło się/s**|Szybkość na sekundę tego żądania podczas przebiegu testu obciążenia dla wystąpień tego żądania, które nie powiodło się.|Nie|
|**Pierwszy czas bajtów**|Średni czas odbierania pierwszego bajtu odpowiedzi, mierzony od momentu wysłania żądania do serwera sieci web. Jednostki są sekundami.|Nie|
|**Czas reakcji**|Średni czas odbierania całej odpowiedzi na żądanie, mierzony od momentu wysłania żądania do serwera sieci web. Jednostki są sekundami.|Tak|
|**Długość zawartości**|Średnia długość treści odpowiedzi na żądanie. Jednostki są bajtami.|Tak|

## <a name="the-tests-table"></a>Tabela Testy

W **tabeli Testy** są wyświetlane szczegóły dotyczące poszczególnych testów uruchamianych podczas testu obciążenia. Tabela zawiera listę testów według testów i scenariuszy, ponieważ jeden test może być uwzględniony w wielu scenariuszach.

W poniższej tabeli wymieniono kolumny w tabeli **Testy.**

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|**Test**|Nazwa testu.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Łącznie**|Całkowita liczba uruchomiono test w scenariuszu. Obejmuje to liczbę razy test przeszedł i nie powiodło się.|Tak|
|**Przekazywane**|Ile razy test został uruchomiony w scenariuszu i przeszedł.|Tak|
|**Niepowodzenie**|Liczba czasu, gdy test został uruchomiony w scenariuszu i nie powiodło się. Wpisy w tej kolumnie są wyświetlane jako hiperłącza. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów w oknie dialogowym **Błędy testu obciążenia.** Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Testy/s**|Szybkość na sekundę testu podczas przebiegu testu obciążenia.|Tak|
|**Przekazany/s**|Szybkość na sekundę tego testu podczas przebiegu testu obciążenia dla wystąpień tego testu, który przeszedł.|Nie|
|**Nie powiodło się/s**|Szybkość na sekundę tego testu podczas przebiegu testu obciążenia dla wystąpień tego testu, które nie powiodły się.|Nie|
|**Czas testu**|Średni czas wykonania testu podczas przebiegu testu obciążenia. Jednostki są sekundami.|Tak|
|**90% czasu testowego**|Wartość 90 percentyla dla czasu testowego.|Nie|
|**95% czasu testowego**|Wartość 95 percentyla dla czasu testowego.|Tak|
|**Żądania/test**|Średnia liczba żądań w teście, jeśli jest to test wydajności sieci web.|Nie|

## <a name="the-transactions-table"></a>Tabela Transakcje

W **tabeli Transakcje** jest wyświetlana lista transakcji, które wystąpiły podczas przebiegu testu obciążenia. Transakcje odnoszą się do transakcji zdefiniowanych w teście wydajności sieci web lub czasomierzy zdefiniowanych w teście jednostkowym. Transakcja nie odwołuje się do transakcji bazy danych.

W poniższej tabeli wymieniono kolumny w tabeli **Transakcje.**

> [!NOTE]
> Aby wyświetlić wszystkie kolumny, należy włączyć właściwość Magazyn szczegółów chronometrażu skojarzoną z ustawieniem aktywnego uruchamiania. Aby uzyskać więcej informacji, zobacz [Jak: Określanie właściwości Magazyn szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Kolumna|Opis|Widoczne bez szczegółów chronometrażu|
|-|-|-|
|**Transakcji**|Nazwa transakcji.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łącznie**|Całkowita liczba transakcji wystawionych podczas przebiegu testu obciążenia.|Tak|
|**Czas transakcji**|Czas wykonania transakcji podczas przebiegu testu obciążenia. W przypadku testów wydajności sieci Web czas myślenia jest uwzględniany w obliczeniach. Jednostki są sekundami.|Nie|
|**Czas reakcji**|Czas odpowiedzi dla transakcji testu wydajności sieci web w przebiegu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czas odpowiedzi nie obejmuje żadnych czasu myślenia, które wystąpiły podczas transakcji. Jednostki są sekundami.|Nie|
|**Ave. Czas transakcji**|Średni czas transakcji. Ten czas obejmuje czasy myślenia. Na przykład jeśli masz trzy żądania i każdy ma czas na myślenie, tym razem będzie zawierać te czasy myślenia i rzeczywisty czas do wykonania żądań.|Nie|
|**Ave. Czas reakcji**|Średni czas odpowiedzi dla transakcji testu wydajności sieci web w przebiegu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czas odpowiedzi nie obejmuje żadnych czasu myślenia, które wystąpiły podczas transakcji. Jednostki są sekundami.|Nie|
|**Minimalny czas reakcji**|Nie obejmuje to czasów myślenia.|Nie|
|**Maksymalny czas reakcji**|Nie obejmuje to czasów myślenia.|Nie|
|**Mediana czasu reakcji**|Nie obejmuje to czasów myślenia.|Nie|
|**90% czasu reakcji**|Wartość 90 percentyla dla czasu transakcji. Nie obejmuje to czasów myślenia. **Uwaga:**  Różni się to od programu Visual Studio Team System 2008 Test Load Agent, który użył **90%** wartość czasu transakcji.|Nie|
|**95% czasu reakcji**|Wartość percentyla 95.dla czasu transakcji. Nie obejmuje to czasów myślenia. **Uwaga:**  Różni się to od programu Visual Studio Team System 2008 Test Load Agent, który użył **95%** wartość czasu transakcji.|Nie|
|**99% czasu reakcji**|99. wartość percentyla dla czasu transakcji. Nie obejmuje to czasów myślenia.|Nie|
|**Czas reakcji dewelopera std**|Nie obejmuje to czasów myślenia.|Nie|

## <a name="the-errors-table"></a>Tabela Błędy

Po uruchomieniu testu obciążenia, można analizować błędy, które występują. Analizowanie błędów i dostosowywanie testów są ważną częścią procesu testowania obciążenia. Jeśli wystąpiły jakiekolwiek błędy, **hiperłącze błędów** pojawia się na pasku stanu testu obciążenia i określa liczbę błędów, które wystąpiły. Aby wyświetlić tabelę błędów, należy wybrać hiperłącze.

Tabela błędów grupuje błędy, które wystąpiły podczas testu obciążenia według typu i podtypu błędu. Istnieje również **wiersz sumy** w tabeli, który określa całkowitą liczbę wszystkich błędów, które wystąpiły.

Tabela błędów zawiera następujące kolumny:

|Kolumna|Opis|Domyślnie widoczny|
|-|-|-|
|Typ|Typ błędu. Na przykład HttpError.|Tak|
|SubType|Podtyp błędu. Na przykład LoadTestException.|Tak|
|Liczba|Liczba błędów tego typu, które wystąpiły podczas testu obciążenia. Wpisy w tej kolumnie są wyświetlane jako hiperłącza. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów.|Tak|
|Ostatnia wiadomość|Komunikat, który opisuje błąd. Na przykład 404 - NotFound.|Tak|

Aby uzyskać więcej informacji, zobacz [Praca z tabelami testów obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Przechodzenie do szczegółów listy błędów

Tabela błędów grupuje błędy według typu i podtypu błędu. Aby wyświetlić tabelę poszczególnych błędów, zostanie wyświetlone okno dialogowe **Błędy testu obciążenia.** Aby wyświetlić okno dialogowe, wybierz hiperłącze w kolumnie **Zliczanie** tabeli błędy. Okno dialogowe można również wyświetlić, klikając prawym przyciskiem myszy wiersz w wypełnionej tabeli błędów i wybierając pozycję **Błędy**.

> [!NOTE]
> Zbierane są tylko pierwsze 1000 wystąpień dowolnego typu błędu i kombinacji podtypu. Podczas **wyświetlania okna** dialogowego Błędy testu obciążenia zobaczysz co najwyżej pierwsze 1000 wystąpień tego błędu.

Tabela **Błędy testu obciążenia** zawiera następujące kolumny:

|Kolumna|Opis|
|-|-|
|**Czas**|Czas podczas testu obciążenia, w którym wystąpił błąd.|
|**Agent**|Nazwa komputera agenta, na którym wystąpił błąd. Jest to ważne podczas uruchamiania testów obciążenia przy użyciu kontrolerów testów i agentów testowych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nazwa testu wydajności sieci web, w którym wystąpił błąd.|
|**Scenariusz**|Nazwa scenariusza, w którym wystąpił błąd.|
|**Żądanie**|Adres URL żądania, w którym wystąpił błąd.|
|**Typ**|Typ błędu. Na przykład HttpError.|
|**Podtypu**|Podtyp błędu. Na przykład LoadTestException.|
|**Tekst**|Tekst komunikatu o błędzie. Na przykład 404 - NotFound.|
|**Stos**|Wpisy w tej kolumnie są puste lub słowo **Stack** jest sformatowany jako hiperłącze. Można wybrać hiperłącze, aby wyświetlić ślad stosu błędu.|
|**Szczegóły**|Wpisy w tej kolumnie są puste lub słowo **TestLog** jest sformatowany jako hiperłącze. To łącze może pomóc wizolowaniu błędów w teście obciążenia. Na przykład wybranie łącza **TestLog** w przypadku błędu żądania testu wydajności sieci web spowoduje otwarcie wyników testu wydajności sieci web w przeglądarce wyników testów wydajności sieci Web i wyróżnienie błędu żądania.|

> [!NOTE]
> Tabelę można sortować, wybierając nagłówki kolumn.

## <a name="the-sql-trace-data-table"></a>Tabela danych śledzenia SQL

Można zbierać dane śledzenia SQL podczas przebiegu testu obciążenia do analizy później. Zbieranie danych śledzenia pozwala zidentyfikować najwolniejsze uruchomione kwerendy i procedury przechowywane w testowanej bazie danych programu SQL Server.

Jeśli śledzenie SQL jest włączone, plik jest tworzony podczas przebiegu testu obciążenia, który zawiera dane śledzenia. Te dane są automatycznie zapisywane w magazynie wyników testu obciążenia na końcu przebiegu testu, a plik śledzenia zostanie usunięty. Analizowanie danych śledzenia w tabeli **śledzenia SQL** po zakończeniu testu obciążenia.

### <a name="to-view-sql-trace-data"></a>Aby wyświetlić dane śledzenia SQL

1. W analizatorze testu obciążenia wybierz pozycję **Tabele** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2. Z listy rozwijanej **Tabela** wybierz pozycję **Śledzenia SQL**.

3. Dane śledzenia, które zostały zebrane podczas uruchamiania jest wyświetlany w siatce. W tabeli wymieniono najwolniej działające operacje SQL posortowane według czasu trwania, z najwolniejszymi u góry. Zazwyczaj **duration** kolumna jest pierwszą kolumną do zbadania. Dane są wyświetlane w milisekundach.

   Wyświetlane kolumny są następujące:

    - **Klasa zdarzenia**

    - **Czas trwania**

    - **Procesora**

    - **Odczytuje**

    - **Zapisuje**

    - **TextData**

    - **Starttime**

    - **EndTime**

   Jeśli chcesz śledzić zdarzenia SQL inne niż dane zidentyfikowane w tych kolumnach, można skonfigurować własne niestandardowe śledzenie SQL za pomocą narzędzia SQL Profiler, niezależnie od programu Visual Studio.

## <a name="tile-load-test-tables"></a>Tabele testów obciążenia kafelków

Podczas wyświetlania wyników przebiegu testu obciążenia można wyświetlić dane jako szczegółowe tabele. Aby przełączyć się do widoku tabeli, wybierz pozycję **Tabele** na pasku narzędzi **testu obciążenia.** Dostępne tabele to **Błędy,** **Strony**, **Żądania,** **Śledzenie SQL,** **Testy,** **Progi**i **Transakcje.** Aby uzyskać więcej informacji, zobacz [Praca z tabelami testów obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

W widoku tabeli można wyświetlać maksymalnie cztery tabele naraz bez nakładania się tabel.

### <a name="to-tile-tables"></a>Do kafelków tabel

1. Na **pasku narzędzi Analizator testu obciążenia** wybierz pozycję **Tabele**.

     Zostanie otwarty widok tabeli. Domyślnym układem są dwa panele poziome.

2. Na **pasku narzędzi Analizator testu obciążenia** wybierz przycisk **układu,** a następnie wybierz jedną z następujących opcji:

    - **Jeden panel**

    - **Dwa panele poziome**

    - **Trzy panele poziome**

    - **Cztery panele poziome**

3. Aby przełączać się między różnymi tabelami, użyj listy rozwijanej nad siatką tabeli w każdym panelu.

    > [!NOTE]
    > Nie można wyświetlić tej samej tabeli w więcej niż jednym panelu. Jeśli tabela wyświetlana w jednym panelu zostanie zmieniona na tabelę już wyświetlaną w innym panelu, tabele zmienią panele.

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testu obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Podsumowanie wyników testu obciążenia](../test/load-test-results-summary-overview.md)
