---
title: Analizowanie wyników testów obciążenia oraz błędów
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98e54e8e1bec7502e7401dc6a13a639e92c1a881
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823044"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli analizatora testu obciążenia

Po wyświetleniu wyników przebiegu testu obciążeniowego można wyświetlić różnych okienek, które udostępniają różne sposoby analizować dane. Dane można wyświetlić jako wykresu, aby zobaczyć, jak zmienia się wraz z upływem czasu, lub można wyświetlić dane jako tabele szczegółów.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby przełączyć się do widoku tabeli, wybierz opcję **tabel** na **testu obciążeniowego** paska narzędzi. Aby przełączyć się między różnymi tabelami, należy użyć **tabeli** listy rozwijanej na pasku narzędzi powyżej siatkę tabeli. W widoku tabeli można wyświetlić maksymalnie cztery tabele w danym momencie. Aby uzyskać więcej informacji, zobacz [tabele testu obciążeniowego kafelka](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) w tym temacie.

Większość wartości liczbowych, wyświetlane w formie tabeli liczników wydajności kumulują się za pośrednictwem przebiegu testu obciążeniowego całego. Kolumny o nazwie **ostatniego** wyjątek stanowią i reprezentować wartość od najnowszych interwału próbkowania.

> [!NOTE]
> Kolumny o nazwie **ostatniego** są dostępne tylko wtedy, gdy test obciążeniowy jest wykonywany. Po zakończeniu testu obciążenia tych kolumn nie są dostępne.

Większość tabel można sortować, wybierając tytuł kolumny, która ma zostać wykonane sortowanie. Domyślnie niektóre tabele nie są wyświetlane wszystkie dostępne kolumny. Jeśli dostępnych kolumn, można dodać do tabel, kolumn. Aby dodać kolumny, kliknij prawym przyciskiem myszy tabelę, a następnie wybierz **Dodaj/Usuń kolumny**.

> [!NOTE]
> Możesz skopiować dane z tabeli do innych aplikacji, takich jak program Excel dodatkowe analizy.

## <a name="the-load-test-tables"></a>Tabele testu obciążenia

Poniższa tabela zawiera listę tabel, które są dostępne do analizowania przebiegów testów obciążeniowych.

|Nazwa tabeli|Opis|
|-|-|
|błędy|Wyświetla listę błędów, które wystąpiły podczas przebiegu testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [tabeli błędów](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) w tym temacie i [wyniki testu obciążenia analizy](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Strony|Wyświetla listę stron dostęp podczas przebiegu testu obciążeniowego. Niektóre dane w tej tabeli jest dostępna tylko wtedy, gdy test obciążenia został ukończony. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie odpowiedzi strony web](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Żądania|Wyświetla szczegóły dotyczące poszczególnych żądań wystawiony podczas testu obciążeniowego. Obejmuje to wszystkie żądania HTTP i zależne żądania, taką jak obrazy. Aby uzyskać więcej informacji, zobacz [tabeli Requests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) w tym temacie.|
|Śledzenie SQL|Wyświetla wyniki śledzenia SQL. Ta tabela jest dostępna tylko w przypadku, po zakończeniu testu obciążenia i tylko wtedy, gdy Śledzenie SQL został użyty podczas testu. Aby uzyskać więcej informacji, zobacz [tabeli danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) w tym temacie.|
|Testy|Wyświetla szczegóły dotyczące indywidualnych testów są uruchamiane podczas testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [tabeli testy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) w tym temacie.|
|Progi|Wyświetla listę naruszeń zasady progu, które wystąpiły podczas przebiegu testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakcje|Wyświetla listę transakcji, które wystąpiły podczas przebiegu testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [tabeli z transakcjami](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) w tym temacie.|
|Agenci|Wyświetla tylko wtedy, gdy test obciążenia jest przy użyciu kontrolera testów i agentów testowych. Wyświetla listę agentów, które były używane podczas przebiegu testu obciążeniowego. Tabela agentów zawiera liczbę żądań, agent przetestowane i tych żądań, jak wiele nie powiodło się. Ponadto tabela agentów obejmuje liczbę testów w asortymencie test testów obciążenia, który agent przetestowany i tych, ile nie powiodło się.|
|Szczegóły testu|Wyświetla szczegóły dotyczące testy w asortymencie test dla testu obciążeniowego. Szczegółowe informacje obejmują nazwę testu, scenariusz, w którym test został, przy uruchomieniu testu, długość czasu, jaki zajęło test, aby uruchomić i wynik testu, wskazując, jeśli test zakończony powodzeniem lub niepowodzeniem. W przypadku niepowodzenia testu link znajduje się w **szczegóły** kolumny. Możesz wybrać łącze, co spowoduje przejście do edytora testów wydajności sieci Web za pomocą żądań zakończonych niepowodzeniem wyróżnione.|

## <a name="collect-percentile-data"></a>Zbieranie danych percentyl

 Niektóre tabele testu obciążenia mogą zawierać dodatkowe kolumny, które obejmują percentyl danych i czasów odpowiedzi podzielonej na grup oparty na emulacji sieci. Te dane nie są zbierane domyślnie. Percentyli jest dostępna tylko w przypadku, gdy zapisujesz wyniki do bazy danych, a nie w przypadku, gdy zapiszesz lokalnie. Aby uzyskać więcej informacji, zobacz [w repozytorium wyników testów obciążenia z wynikami testów obciążeniowych zarządzanie](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ponadto aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz konkretny uruchamiania węzła Ustawienia można zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **StatisticsOnly** lub **AllIndividualDetails**. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie odpowiedzi strony web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabela żądań

 **Żądań** tabela zawiera szczegóły dotyczące poszczególnych żądań wystawiony podczas testu obciążeniowego. Obejmuje to wszystkie żądania HTTP i zależne żądania, taką jak obrazy. W tabeli wymieniono żądań za pomocą testu i scenariusza, ponieważ jedno żądanie mogą być zawarte w wielu testów i scenariuszy.

 W poniższej tabeli wymieniono w kolumnach **żądań** tabeli:

|Kolumny|Opis|Domyślnie widoczny|
|-|-|-|
|**Żądanie**|Adres URL żądania. Na przykład *home.html*, lub *arrow.gif pomarańczowy*.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łączna liczba**|Łączna liczba to żądanie testu wydajności sieci web wydane podczas testu obciążeniowego przebiegu. Suma zawiera udanych i nieudanych żądań, ale nie obejmuje żądań z pamięci podręcznej, ponieważ nie zostały przekazane do serwera sieci web.|Tak|
|**Przekazany**|Ile razy żądanie zostało wystawione i przekazywane.|Nie|
|**Niepowodzenie**|Liczba przypadków, żądania został wystawiony i nie powiodło się. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególne błędy w **błędy testu obciążenia** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wyniki testu obciążenia analizy](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Pamięci podręcznej**|Całkowita liczba przypadków, gdy żądanie już był buforowany.|Nie|
|**Żądań na sekundę**|Częstotliwość żądania podczas przebiegu testu obciążeniowego.|Nie|
|**Przekazany na sekundę**|Częstotliwość tego żądania podczas testu obciążenia Uruchom wystąpień tego żądania, które przekazane.|Nie|
|**Nie powiodło się na sekundę**|Częstotliwość tego żądania podczas testu obciążenia Uruchom wystąpień tego żądania, który uległ awarii.|Nie|
|**Czas pierwszego bajtu**|Średni czas odebrania pierwszego bajtu odpowiedzi, mierzony od momentu w którym żądanie zostało wysłane do serwera sieci web. Jednostki są w ciągu kilku sekund.|Nie|
|**Czas odpowiedzi**|Średni czas na odebranie całej odpowiedzi na żądanie, mierzony od momentu w którym żądanie zostało wysłane do serwera sieci web. Jednostki są w ciągu kilku sekund.|Tak|
|**Długość zawartości**|Średnia długość zawartości odpowiedzi na żądanie. Jednostki są w bajtach.|Tak|

## <a name="the-tests-table"></a>Tabela testów

 **Testy** tabela zawiera szczegóły przypadku indywidualnych testów uruchamianych podczas testu obciążeniowego. W tabeli wymieniono testy według testu i scenariusza, ponieważ jeden test mogą być zawarte w wielu scenariuszach.

 W poniższej tabeli wymieniono w kolumnach **testy** tabeli.

|Kolumny|Opis|Domyślnie widoczny|
|-|-|-|
|**Test**|Nazwa testu.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Łączna liczba**|Całkowita liczba przypadków, gdy test został uruchomiony w scenariuszu. W tym liczba testu przekazywane, a nie powiodło się.|Tak|
|**Przekazany**|Liczba przypadków, testu zostało wykonane w scenariuszu i przekazywane.|Tak|
|**Niepowodzenie**|Liczba przypadków, test zostało wykonane w scenariuszu, a nie powiodło się. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególne błędy w **błędy testu obciążenia** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wyniki testu obciążenia analizy](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Tests/Sec**|Częstotliwość testu podczas przebiegu testu obciążeniowego.|Tak|
|**Przekazany na sekundę**|Stawka za sekundę ten test podczas testu obciążenia Uruchom wystąpień tego testu, które przekazane.|Nie|
|**Nie powiodło się na sekundę**|Stawka za sekundę ten test podczas testu obciążenia Uruchom wystąpień tego testu, który uległ awarii.|Nie|
|**Czas testu**|Średni czas wykonania testu podczas przebiegu testu obciążeniowego. Jednostki są w ciągu kilku sekund.|Tak|
|**90% czasu testu**|Wartość 90. percentyla dla czasu testu.|Nie|
|**95% czasu testu**|Wartość 95. percentyla dla czasu testu.|Tak|
|**Żądania i testowania**|Średnia liczba żądań w teście, jeśli jest wydajności sieci web testów.|Nie|

## <a name="the-transactions-table"></a>Tabela transakcji

 **Transakcji** tabela zawiera listę transakcji, które wystąpiły podczas przebiegu testu obciążeniowego. Transakcje odnoszą się do transakcji zdefiniowanych w teście wydajności sieci web lub czasomierzy zdefiniowanych w test jednostkowy. Transakcja nie odwołuje się do transakcji bazodanowych.

 W poniższej tabeli wymieniono w kolumnach **transakcji** tabeli.

> [!NOTE]
> Aby wyświetlić wszystkie kolumny, należy włączyć właściwości przechowywanie informacji, które jest skojarzone z aktywnego parametru uruchomieniowego. Aby uzyskać więcej informacji, zobacz [jak: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Kolumna|Opis|Widoczna bez szczegółowych informacji o czasie|
|-|-|-|
|**Transakcja**|Nazwa transakcji.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Łączna liczba**|Całkowita liczba transakcji, które odbyły się podczas przebiegu testu obciążeniowego.|Tak|
|**Czas transakcji**|Czas wykonania transakcji podczas przebiegu testu obciążeniowego. Dla testów wydajności sieci web, myśl w obliczeniach zawarty jest czas. Jednostki są w ciągu kilku sekund.|Nie|
|**Czas odpowiedzi**|Czas odpowiedzi transakcji testu wydajności sieci web w przebiegu testu obciążeniowego. Czas odpowiedzi różni się od czasu transakcji, czas odpowiedzi nie zawiera żadnych reakcji czas, który wystąpił podczas wykonywania tej transakcji. Jednostki są w ciągu kilku sekund.|Nie|
|**Średnio Czas transakcji**|Średni czas transakcji. Tym razem zawiera czasy reakcji. Na przykład jeśli masz trzech żądań i każdy z nich ma czas namysłu, tym razem będzie zawierać te czasy reakcji i rzeczywisty czas wykonywania żądania.|Nie|
|**Średnio Czas odpowiedzi**|Średni czas odpowiedzi transakcji testu wydajności sieci web w przebiegu testu obciążeniowego. Czas odpowiedzi różni się od czasu transakcji, czas odpowiedzi nie zawiera żadnych reakcji czas, który wystąpił podczas wykonywania tej transakcji. Jednostki są w ciągu kilku sekund.|Nie|
|**Najmniejszy czas odpowiedzi**|Nie dotyczy to czasy reakcji.|Nie|
|**Największy czas odpowiedzi**|Nie dotyczy to czasy reakcji.|Nie|
|**Mediana czasu odpowiedzi**|Nie dotyczy to czasy reakcji.|Nie|
|**90% czasu odpowiedzi**|Wartość 90. percentyla dla czasu transakcji. Nie dotyczy to czasy reakcji. **Uwaga:**  To różni się od agenta Visual Studio Team System 2008 testu obciążenia, które używane **90% czasu transakcji** wartość.|Nie|
|**95% czasu odpowiedzi**|Wartość 95. percentyla dla czasu transakcji. Nie dotyczy to czasy reakcji. **Uwaga:**  To różni się od agenta Visual Studio Team System 2008 testu obciążenia, które używane **95% czasu transakcji** wartość.|Nie|
|**99% czasu odpowiedzi**|99. percentyl wartość czasu transakcji. Nie dotyczy to czasy reakcji.|Nie|
|**Odchylenie standardowe czasu odpowiedzi**|Nie dotyczy to czasy reakcji.|Nie|

## <a name="the-errors-table"></a>W tabeli błędów

 Po uruchomieniu testu obciążenia, można analizować występujące błędy. Analizowanie błędów i dostosowywanie testów są ważną częścią procesu testu obciążenia. Jeśli wystąpiły błędy, **błędy** hiperłącze pojawia się na pasku stanu testu obciążenia i określa liczbę błędów, które wystąpiły. Aby wyświetlić tabelę błędy, możesz wybrać hiperłącze.

 Błędy tabeli grup błędów, które wystąpiły podczas ładowania testów przez typ i podtyp błędu. Istnieje również **całkowita** wiersza w tabeli, określający łączna liczba błędów, które wystąpiły.

 Tabela błędów zawiera następujące kolumny:

|Kolumny|Opis|Domyślnie widoczny|
|-|-|-|
|Typ|Typ błędu. Na przykład HttpError.|Tak|
|SubType|Podtyp błędu. Na przykład LoadTestException.|Tak|
|Liczba|Liczba błędów tego typu, który wystąpił podczas testu obciążeniowego. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych błędów.|Tak|
|Ostatni komunikat|Komunikat, który opisuje błąd. Na przykład 404 - NotFound.|Tak|

 Aby uzyskać więcej informacji, zobacz [Praca z tabelami testu obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Przejdź do szczegółów listy błędów

Błędy tabeli grup błędów, typ i podtyp błędu. Aby wyświetlić tabelę poszczególne błędy, możesz wyświetlić **błędy testu obciążenia** okno dialogowe. Aby wyświetlić okno dialogowe, wybierz hiperłącze w **liczba** kolumny w tabeli błędów. Można również wyświetlić okno dialogowe, kliknij prawym przyciskiem myszy wiersz w tabeli błędów, które jest wypełniana i wybierając pozycję **błędy**.

> [!NOTE]
> Zbierane są tylko pierwsze 1000 wystąpień dowolnej kombinacji typem i podtypem błędu. Po wyświetleniu **błędy testu obciążenia** okno dialogowe, zostanie wyświetlony co najwyżej pierwsze 1000 wystąpienia tego błędu.

**Błędy testu obciążenia** tabeli zawiera następujące kolumny:

|Kolumny|Opis|
|-|-|
|**czas**|Czas podczas ładowania testu w którym wystąpił błąd.|
|**Agent**|Nazwa komputera agenta, na którym wystąpił błąd. Jest to ważne w przypadku uruchamiania testów obciążenia z wykorzystaniem kontrolerów testów i agentów testowych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nazwa wydajności sieci web testu, w którym wystąpił błąd.|
|**Scenariusz**|Nazwa scenariusza, w którym wystąpił błąd.|
|**Żądanie**|Adres URL żądania, w którym wystąpił błąd.|
|**Typ**|Typ błędu. Na przykład HttpError.|
|**SubType**|Podtyp błędu. Na przykład LoadTestException.|
|**Text**|Tekst komunikatu o błędzie. Na przykład 404 - NotFound.|
|**Stos**|W tej kolumnie są puste lub słowo **stosu** jest sformatowana jako hiperłącze. Możesz wybrać hiperlink, aby wyświetlić ślad stosu błędu.|
|**Szczegółowe informacje**|W tej kolumnie są puste lub słowo **TestLog** jest sformatowana jako hiperłącze. Ten link może pomóc wyizolować błędy w teście obciążeniowym. Na przykład wybranie **TestLog** łącze na błąd żądania testu wydajności sieci web spowoduje to otwarcie wyniki dla testów wydajności sieci web w sieci Web podgląd wyników testu wydajności i wyróżnić błąd żądania.|

> [!NOTE]
> Możesz sortować tabeli, wybierając nagłówków kolumn.

## <a name="the-sql-trace-data-table"></a>Tabela danych śledzenia SQL

Można zbierać dane śledzenia SQL podczas testu obciążenia do dalszej analizy. Zbieranie danych śledzenia umożliwia identyfikowanie najwolniej uruchomionych zapytań i procedur składowanych w bazie danych programu SQL Server, testowany.

Jeśli włączone jest śledzenie SQL, plik jest tworzony podczas testu obciążenia zawierającego dane śledzenia. Te dane są automatycznie zapisywane w Store wyników testu obciążenia na końcu przebiegu testowego, a plik śledzenia zostanie usunięty. Analizowanie danych śledzenia w **śledzenia SQL** tabeli po zakończeniu testu obciążenia.

### <a name="to-view-sql-trace-data"></a>Aby wyświetlić dane śledzenia SQL

1. W analizatorze testu obciążenia wybierz **tabel** na pasku narzędzi, aby upewnić się, że wyświetlana jest siatka tabeli.

2. W **tabeli** listy rozwijanej wybierz pozycję **śledzenia SQL**.

3. Dane śledzenia, które zostały zebrane podczas uruchomienia jest wyświetlany w siatce. W tabeli wymieniono najwolniej uruchomionej operacji SQL, posortowane według czasu trwania z najwolniejsze u góry. Zazwyczaj **czas trwania** kolumna jest pierwszej kolumny do sprawdzenia. Dane są wyświetlane w milisekundach.

   Kolumny wyświetlane są następujące:

    - **Event — klasa**

    - **Czas trwania**

    - **CPU**

    - **Odczytuje**

    - **Operacje zapisu**

    - **Kolumna TextData**

    - **Godzina rozpoczęcia**

    - **Czas zakończenia**

   Śledzenie zdarzeń SQL inne niż dane w tych kolumnach, możesz skonfigurować własne niestandardowe śledzenia SQL za pomocą narzędzia SQL Profiler, niezależnie od programu Visual Studio.

## <a name="tile-load-test-tables"></a>Tabele testu obciążeniowego kafelka

Po wyświetleniu wyników przebiegu testu obciążeniowego można wyświetlić dane jako tabele szczegółów. Aby przełączyć się do widoku tabeli, wybierz opcję **tabel** na **testu obciążeniowego** paska narzędzi. Tabele, które są dostępne są **błędy**, **stron**, **żądań**, **śledzenia SQL**, **testy**,  **Progi**, i **transakcji**. Aby uzyskać więcej informacji, zobacz [Praca z tabelami testu obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

W widoku tabeli można wyświetlić maksymalnie cztery tabele w czasie, bez tabel nakładających się.

### <a name="to-tile-tables"></a>Na kafelku tabel

1. Na **analizatora testu obciążenia** narzędzi, wybierz **tabel**.

     Zostanie otwarty widok tabeli. Układ domyślny to dwa panele poziome.

2. Na **analizatora testu obciążenia** narzędzi, wybierz **układ** przycisk, a następnie wybierz jedno z następujących opcji:

    - **Jeden Panel**

    - **Dwa panele poziome**

    - **Trzy panele poziome**

    - **Cztery panele poziome**

3. Aby przełączyć się między różnymi tabelami, użyj listy rozwijanej powyżej siatki tabeli w każdym panelu.

    > [!NOTE]
    > Nie można wyświetlić tej samej tabeli w więcej niż jeden panel. W przypadku zmiany tabeli wyświetlane w jeden panel już wyświetlane w panelu inną tabelę tabel Przełącz paneli.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Wyniki testu obciążeniowego dostęp do analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Przegląd podsumowania wyników testu obciążenia](../test/load-test-results-summary-overview.md)