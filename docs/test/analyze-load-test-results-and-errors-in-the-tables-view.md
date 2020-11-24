---
title: Analizowanie Wyniki testów obciążenia i błędów
description: Dowiedz się, jak wyświetlać okienka, które udostępniają różne sposoby analizowania wyników przebiegu testu obciążenia, na przykład grafu w czasie lub tabelach szczegółowych.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7787b3b0afaed0bc3592b458646b97151e309905
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442511"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia i błędów w widoku tabele analizatora testu obciążenia

Podczas przeglądania wyników przebiegu testu obciążenia można wyświetlić różne okienka, które udostępniają różne sposoby analizowania danych. Dane można wyświetlić jako Graf, aby zobaczyć, jak zmienia się w czasie, lub wyświetlić dane jako tabele szczegółowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby przełączyć się do widoku tabeli, wybierz **tabele** na pasku narzędzi **testu obciążenia** . Aby przełączać się między różnymi tabelami, Użyj listy rozwijanej **tabela** na pasku narzędzi powyżej siatki tabeli. W widoku tabeli można wyświetlić do czterech tabel jednocześnie. Aby uzyskać więcej informacji, zobacz [tabele testów obciążenia kafelków](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) w tym temacie.

Większość wartości liczbowych wyświetlanych w tabeli dla liczników wydajności jest zbiorcza dla całego przebiegu testu obciążenia. Kolumny o nazwie **Last** są wyjątkiem i reprezentują wartość z ostatniego interwału próbkowania.

> [!NOTE]
> Kolumny o nazwie **Last** są dostępne tylko podczas wykonywania testu obciążenia. Po zakończeniu testu obciążenia te kolumny są niedostępne.

Większość tabel można sortować, wybierając tytuł kolumny, według której ma zostać wykonane sortowanie. Domyślnie w niektórych tabelach nie są wyświetlane wszystkie dostępne kolumny. Kolumny można dodawać do tabel, jeśli są dostępne kolumny. Aby dodać kolumny, kliknij ją prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj/Usuń kolumny**.

> [!NOTE]
> Dane z tabeli można kopiować do innych aplikacji, takich jak program Excel, w celu uzyskania dodatkowej analizy.

## <a name="the-load-test-tables"></a>Tabele testu obciążenia

Poniższa tabela zawiera listę tabel, które są dostępne do analizowania przebiegów testów obciążenia.

|Nazwa tabeli|Opis|
|-|-|
|błędy|Wyświetla listę błędów, które wystąpiły podczas przebiegu testu obciążenia. Więcej informacji można znaleźć w [tabeli błędy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) w tym temacie i [analizować wyniki testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Strony|Wyświetla listę stron, do których można uzyskać dostęp podczas przebiegu testu obciążenia. Niektóre dane w tej tabeli są dostępne dopiero po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [How to: View Web Page Response](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Żądania|Wyświetla szczegółowe informacje o poszczególnych żądaniach wystawionych podczas testu obciążenia. Obejmuje to wszystkie żądania HTTP, a także żądania zależne, takie jak obrazy. Więcej informacji znajduje się w [tabeli Requests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) w tym temacie.|
|Śledzenie SQL|Wyświetla wyniki śledzenia SQL. Ta tabela jest dostępna dopiero po zakończeniu testu obciążenia i tylko wtedy, gdy podczas testu użyto śledzenia SQL. Aby uzyskać więcej informacji, zobacz [tabelę danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) w tym temacie.|
|Testy|Wyświetla szczegóły poszczególnych testów wykonywanych w trakcie testu obciążenia. Aby uzyskać więcej informacji, zobacz [tabelę testów](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) w tym temacie.|
|Progi|Wyświetla listę naruszeń reguł progowych, które wystąpiły podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakcje|Wyświetla listę transakcji, które wystąpiły podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [tabela transakcji](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) w tym temacie.|
|Agenci|Jest wyświetlany tylko wtedy, gdy test obciążenia korzysta z kontrolera testów i agentów testowych. Wyświetla listę agentów, które były używane podczas przebiegu testu obciążenia. Tabela agenci zawiera liczbę żądań przetestowanych przez agenta oraz o te żądania, jak wiele z nich nie powiodło się. Ponadto tabela agenci zawiera liczbę testów w teście testów obciążenia, które zostały przetestowane przez agenta, a także o tym, ile nie powiodło się.|
|Szczegóły testu|Wyświetla szczegóły testów zamieszczonych w teście mieszanym dla testu obciążenia. Szczegóły obejmują nazwę testu, scenariusz, w którym przeprowadzono test, czas rozpoczęcia testu, długość czasu, przez który przeszedł test, oraz wynik testu wskazujący, czy test zakończył się powodzeniem, czy nie. Jeśli test nie powiódł się, w kolumnie **szczegóły** znajduje się link. Możesz wybrać link, który przeprowadzi Cię do Edytor internetowego testu wydajnościowego z wyróżnionym żądaniem zakończonym niepowodzeniem.|

## <a name="collect-percentile-data"></a>Zbierz dane percentylu

Niektóre tabele testów obciążenia mogą zawierać dodatkowe kolumny, które obejmują dane percentylu i czasy odpowiedzi podzielone na grupy na podstawie emulacji sieci. Domyślnie te dane nie są zbierane. Dane percentylu są dostępne tylko wtedy, gdy zapisujesz wyniki w bazie danych, a nie w przypadku zapisywania lokalnego. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyniki testów ładowania](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ponadto aby zebrać te dane, w **Edytor testu obciążeniowego** w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchamiania, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **StatisticsOnly** lub **AllIndividualDetails**. Aby uzyskać więcej informacji, zobacz [How to: View Web Page Response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabela żądań

W tabeli **żądań** są wyświetlane szczegółowe informacje o poszczególnych żądaniach wystawionych podczas testu obciążenia. Obejmuje to wszystkie żądania HTTP, a także żądania zależne, takie jak obrazy. W tabeli wymieniono żądania według testu i scenariusza, ponieważ jedno żądanie może być zawarte w wielu testach i scenariuszach.

W poniższej tabeli wymieniono kolumny w tabeli **Requests** :

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|**Żądanie**|Adres URL żądania. Na przykład *home.html* lub *orange-arrow.gif*.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łącznie**|Całkowita liczba żądań testu wydajności sieci Web wystawionych podczas przebiegu testu obciążenia. Suma obejmuje żądania zakończone powodzeniem i nieudane, ale nie obejmuje buforowanych żądań, ponieważ nie są wystawiane dla serwera sieci Web.|Tak|
|**Przeniesione**|Liczba przypadków, gdy żądanie zostało wystawione i zakończone.|Nie|
|**Niepowodzenie**|Liczba przypadków wystawienia żądania i niepowodzenia. Wpisy w tej kolumnie są wyświetlane jako hiperlinki. Możesz wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów w oknie dialogowym **Błędy testu obciążenia** . Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**W pamięci podręcznej**|Łączna liczba przypadków, gdy żądanie zostało już w pamięci podręcznej.|Nie|
|**Liczba żądań na sekundę**|Częstotliwość żądania w trakcie przebiegu testu obciążenia.|Nie|
|**Liczba przesłanych/s**|Częstotliwość tego żądania podczas przebiegu testu obciążenia dla wystąpień tego żądania, które zakończono.|Nie|
|**Niepowodzenie/s**|Częstotliwość tego żądania w trakcie przebiegu testu obciążenia dla wystąpień tego żądania, które się nie powiodły.|Nie|
|**Czas pierwszego bajtu**|Średni czas odebrania pierwszego bajtu odpowiedzi mierzony od momentu wysłania żądania do serwera sieci Web. Jednostki są sekundy.|Nie|
|**Czas odpowiedzi**|Średni czas uzyskiwania całej odpowiedzi na żądanie, mierzoną od momentu wysłania żądania do serwera sieci Web. Jednostki są sekundy.|Tak|
|**Długość zawartości**|Średnia długość zawartości odpowiedzi na żądanie. Jednostki są bajtami.|Tak|

## <a name="the-tests-table"></a>Tabela testów

W tabeli **testów** są wyświetlane szczegóły poszczególnych testów uruchamianych podczas testu obciążenia. W tabeli przedstawiono testy według testu i scenariusza, ponieważ jeden test można uwzględnić w wielu scenariuszach.

W poniższej tabeli przedstawiono kolumny w tabeli **testy** .

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|**Test**|Nazwa testu.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Łącznie**|Całkowita liczba uruchomień testu w scenariuszu. Obejmuje to liczbę testów zakończonych powodzeniem i nieudanych.|Tak|
|**Przeniesione**|Liczba uruchomień testu w scenariuszu i zakończonych niepowodzenie.|Tak|
|**Niepowodzenie**|Liczba uruchomień testu w scenariuszu i nie powiodła się. Wpisy w tej kolumnie są wyświetlane jako hiperlinki. Możesz wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów w oknie dialogowym **Błędy testu obciążenia** . Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Testy/s**|Częstotliwość testu podczas przebiegu testu obciążenia.|Tak|
|**Liczba przesłanych/s**|Częstotliwość tego testu podczas przebiegu testu obciążenia dla wystąpień tego testu, który zakończono.|Nie|
|**Niepowodzenie/s**|Częstotliwość tego testu podczas przebiegu testu obciążenia dla wystąpień tego testu, które zakończyły się niepowodzeniem.|Nie|
|**Czas testu**|Średni czas wykonywania testu podczas przebiegu testu obciążenia. Jednostki są sekundy.|Tak|
|**90% czasu testu**|90 wartość percentylu dla czasu testu.|Nie|
|**95% czasu testu**|Wartość percentylu używany 95. dla czasu testu.|Tak|
|**Żądania/testowanie**|Średnia liczba żądań w teście, jeśli jest to test wydajności sieci Web.|Nie|

## <a name="the-transactions-table"></a>Tabela transakcji

W tabeli **transakcji** jest wyświetlana lista transakcji, które wystąpiły podczas przebiegu testu obciążenia. Transakcje odnoszą się do transakcji zdefiniowanych w teście wydajności sieci Web lub czasomierzy zdefiniowane w teście jednostkowym. Transakcja nie odwołuje się do transakcji bazy danych.

W poniższej tabeli wymieniono kolumny w tabeli **transakcji** .

> [!NOTE]
> Aby wyświetlić wszystkie kolumny, należy włączyć właściwość przechowywania informacji o chronometrażu skojarzoną z aktywnym ustawieniem Run. Aby uzyskać więcej informacji, zobacz [How to: Określ właściwość Storage Details](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Kolumna|Opis|Widoczne bez szczegółów czasu|
|-|-|-|
|**Transakcja**|Nazwa transakcji.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łącznie**|Całkowita liczba transakcji wydanych podczas przebiegu testu obciążenia.|Tak|
|**Czas transakcji**|Czas wykonywania transakcji podczas przebiegu testu obciążenia. W przypadku testów wydajności sieci Web czas reakcji jest uwzględniany w obliczeniach. Jednostki są sekundy.|Nie|
|**Czas odpowiedzi**|Czas odpowiedzi dla transakcji testów wydajności sieci Web w przebiegu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czasie odpowiedzi nie obejmuje żadnych czasów reakcji, które wystąpiły podczas transakcji. Jednostki są sekundy.|Nie|
|**Godzina transakcji**|Średni czas transakcji. Ta godzina obejmuje czasy reakcji. Na przykład jeśli masz trzy żądania, a każdy z nich ma czas reakcji, ten czas będzie obejmował te czasy reakcji i rzeczywisty czas wykonywania żądań.|Nie|
|**Godzina wypowiedzenia**|Średni czas odpowiedzi dla transakcji testów wydajności sieci Web w przebiegu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czasie odpowiedzi nie obejmuje żadnych czasów reakcji, które wystąpiły podczas transakcji. Jednostki są sekundy.|Nie|
|**Minimalny czas odpowiedzi**|Nie obejmuje to czasów reakcji.|Nie|
|**Maksymalny czas odpowiedzi**|Nie obejmuje to czasów reakcji.|Nie|
|**Średni czas odpowiedzi**|Nie obejmuje to czasów reakcji.|Nie|
|**90% czasu odpowiedzi**|90 wartość percentylu dla czasu transakcji. Nie obejmuje to czasów reakcji. **Uwaga:**  To różni się od agenta ładowania testowego programu Visual Studio Team System 2008, który używał wartości **czasu transakcji 90%** .|Nie|
|**95% czasu odpowiedzi**|Wartość percentylu używany 95. dla czasu transakcji. Nie obejmuje to czasów reakcji. **Uwaga:**  To różni się od agenta ładowania testowego programu Visual Studio Team System 2008, który używał wartości **czasu transakcji 95%** .|Nie|
|**99% czasu odpowiedzi**|Wartość percentylu 99 dla czasu transakcji. Nie obejmuje to czasów reakcji.|Nie|
|**Standardowy czas odpowiedzi dla dev**|Nie obejmuje to czasów reakcji.|Nie|

## <a name="the-errors-table"></a>Tabela błędów

Po uruchomieniu testu obciążenia można analizować błędy, które wystąpiły. Analizowanie błędów i dostosowywanie testów jest ważną częścią procesu testu obciążenia. Jeśli wystąpią jakieś błędy, hiperlink **Błędy** pojawia się na pasku stanu testu obciążenia i określa liczbę błędów, które wystąpiły. Aby wyświetlić tabelę błędy, należy wybrać hiperłącze.

Tabela błędy grupuje błędy, które wystąpiły podczas testu obciążenia przez typ i podtyp błędu. W tabeli znajduje się również **całkowita** linia, która określa łączną liczbę wszystkich błędów, które wystąpiły.

Tabela błędy zawiera następujące kolumny:

|Kolumna|Opis|Domyślnie widoczny|
|-|-|-|
|Typ|Typ błędu. Na przykład HttpError.|Tak|
|Podtyp|Podtyp błędu. Na przykład LoadTestException.|Tak|
|Liczba|Liczba błędów tego typu, które wystąpiły podczas testu obciążenia. Wpisy w tej kolumnie są wyświetlane jako hiperlinki. Możesz wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów.|Tak|
|Ostatni komunikat|Komunikat, który opisuje błąd. Na przykład 404-NotFound.|Tak|

Aby uzyskać więcej informacji, zobacz [Praca z tabelami testów obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Przejdź do szczegółów listy błędów

Tabela błędy grupuje błędy według typu i podtyp błędu. Aby wyświetlić tabelę poszczególnych błędów, należy wyświetlić okno dialogowe **Błędy testu obciążenia** . Aby wyświetlić okno dialogowe, wybierz hiperłącze w kolumnie **Liczba** tabeli błędy. Możesz również wyświetlić okno dialogowe, klikając prawym przyciskiem myszy wiersz w tabeli błędy, która została wypełniona, a następnie wybierając **Błędy**.

> [!NOTE]
> Zbierane są tylko pierwsze 1 000 wystąpień dowolnego typu błędu i kombinacji podtypu. Po wyświetleniu okna dialogowego **Błędy testu obciążenia** zobaczysz najwyżej pierwsze wystąpienie 1 000, które wystąpi błąd.

Tabela **Błędy testu obciążenia** zawiera następujące kolumny:

|Kolumna|Opis|
|-|-|
|**Godzina**|Czas podczas testu obciążenia, w którym wystąpił błąd.|
|**Agent**|Nazwa komputera agenta, na którym wystąpił błąd. Jest to ważne w przypadku uruchamiania testów obciążenia za pomocą kontrolerów testów i agentów testowych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nazwa testu wydajności sieci Web, w którym wystąpił błąd.|
|**Scenariusz**|Nazwa scenariusza, w którym wystąpił błąd.|
|**Żądanie**|Adres URL żądania, w którym wystąpił błąd.|
|**Typ**|Typ błędu. Na przykład HttpError.|
|**Podtyp**|Podtyp błędu. Na przykład LoadTestException.|
|**Tekst**|Tekst komunikatu o błędzie. Na przykład 404-NotFound.|
|**Stos**|Wpisy w tej kolumnie są puste lub **stos** słów jest sformatowany jako hiperlink. Możesz wybrać hiperłącze, aby wyświetlić ślad stosu błędu.|
|**Szczegóły**|Wpisy w tej kolumnie są puste lub słowo **TestLog** jest sformatowane jako hiperlink. Ten link może ułatwić wyizolowanie błędów w teście obciążenia. Na przykład wybranie linku **TestLog** na żądanie testu wydajności sieci Web spowoduje otwarcie wyników testu wydajności sieci Web w przeglądarce wyniki testów wydajności sieci Web i wyróżnienie błędu żądania.|

> [!NOTE]
> Tabelę można sortować, wybierając nagłówki kolumn.

## <a name="the-sql-trace-data-table"></a>Tabela danych śledzenia SQL

Dane śledzenia SQL można zbierać podczas przebiegu testu obciążenia w celu późniejszego przeanalizowania. Zbieranie danych śledzenia umożliwia zidentyfikowanie najwolniejszych uruchomionych zapytań i procedur składowanych w testowanej bazie danych SQL Server.

Jeśli śledzenie SQL jest włączone, plik jest tworzony podczas przebiegu testu obciążenia, który zawiera dane śledzenia. Te dane są automatycznie zapisywane w magazynie Wyniki testów obciążenia po zakończeniu przebiegu testu, a plik śledzenia jest usuwany. Dane śledzenia można analizować w tabeli **śledzenia SQL** po zakończeniu testu obciążenia.

### <a name="to-view-sql-trace-data"></a>Aby wyświetlić dane śledzenia SQL

1. W analizatorze testu obciążenia wybierz **tabele** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2. W polu listy rozwijanej **tabela** wybierz pozycję **śledzenie SQL**.

3. Dane śledzenia, które zostały zebrane podczas uruchamiania, są wyświetlane w siatce. W tabeli wymieniono najwolniejsze uruchomione operacje SQL, które są posortowane według czasu trwania, najwolniejszie na górze. Zwykle kolumna **Duration** jest pierwszą kolumną do sprawdzenia. Dane są wyświetlane w milisekundach.

   Wyświetlane są następujące kolumny:

    - **Event — Klasa**

    - **Czas trwania**

    - **Procesor CPU**

    - **Odczyty**

    - **Zapisy**

    - **TextData**

    - **Rozpoczęcia**

    - **EndTime**

   Jeśli chcesz śledzić zdarzenia SQL inne niż dane określone w tych kolumnach, możesz skonfigurować własne niestandardowe śledzenie SQL za pomocą narzędzia SQL Profiler, niezależnie od programu Visual Studio.

## <a name="tile-load-test-tables"></a>Tabele testów obciążenia kafelków

Po wyświetleniu wyników przebiegu testu obciążenia można wyświetlić dane jako tabele szczegółowe. Aby przełączyć się do widoku tabeli, wybierz **tabele** na pasku narzędzi **testu obciążenia** . Dostępne tabele to **Błędy**, **strony**, **żądania**, **śledzenie SQL**, **testy**, **progi** i **transakcje**. Aby uzyskać więcej informacji, zobacz [Praca z tabelami testów obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

W widoku tabeli można wyświetlić do czterech tabel jednocześnie bez nakładania się tabel.

### <a name="to-tile-tables"></a>Do kafelków tabel

1. Na pasku narzędzi **analizatora testu obciążenia** wybierz **tabele**.

     Zostanie otwarty widok tabeli. Układ domyślny to dwa panele poziome.

2. Na pasku narzędzi **analizatora testu obciążenia** wybierz przycisk **Układ** , a następnie wybierz jedną z następujących opcji:

    - **Jeden panel**

    - **Dwa panele poziome**

    - **Trzy panele poziome**

    - **Cztery panele poziome**

3. Aby przełączać się między różnymi tabelami, Użyj listy rozwijanej powyżej siatki tabeli na każdym panelu.

    > [!NOTE]
    > Nie można wyświetlić tej samej tabeli w więcej niż jednym panelu. Jeśli zmienisz tabelę wyświetlaną w jednym panelu do tabeli już wyświetlanej w innym panelu, panele przełączania tabel.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Podsumowanie wyników testów obciążenia — Przegląd](../test/load-test-results-summary-overview.md)
