---
title: Podsumowanie wyników testów obciążenia — Przegląd
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7df3324c2182c376cb9547a4192fca3e601b3dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75584494"
---
# <a name="load-test-results-summary-overview"></a>Podsumowanie wyników testów obciążenia — Przegląd

Po uruchomieniu testu obciążenia można wyświetlić podsumowanie testu obciążenia, aby szybko zrozumieć wyniki. Podsumowanie testu obciążenia zapewnia kluczowe wyniki w formacie kompaktowym i łatwym do odczytu. Możesz również wydrukować podsumowanie testu obciążenia. Sprawia to, że jest to wygodne do użycia podczas przekazywania wyników do zainteresowanych stron. Podsumowanie testu obciążenia jest również widokiem domyślnym, gdy otworzysz wynik testu obciążenia z poprzedniego przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [jak: uzyskiwanie dostępu do wyników testów obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md).

![Widok podsumowania](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Podsumowanie testu obciążenia

Podsumowanie testu obciążenia jest podzielone na sekcje. Początkowe sekcje pojawiają się u góry podsumowania i są zawsze widoczne. Po wyświetleniu podsumowania testu obciążenia najpierw są potrzebne następujące elementy:

- Informacje o przebiegu testu

- Wyniki ogólne

- Kluczowe statystyki: 5 najwolniejszych stron

- Kluczowe statystyki: 5 najwolniejszych testów

- Kluczowe statystyki: 5 najwolniejszych operacji SQL

    > [!NOTE]
    > Sekcja operacje SQL jest wyświetlana tylko wtedy, gdy śledzenie SQL jest włączone w teście obciążenia.

Sekcje zamykające pojawiają się na końcu podsumowania i można je zwinąć, aby zaoszczędzić miejsce. Następujące elementy pojawiają się na końcu podsumowania testu obciążenia:

- Wyniki tekstu

- Wyniki strony

- Wyniki transakcji

- Zasoby testowe systemu

- Zasoby kontrolera i agenta

- błędy

## <a name="test-run-information"></a>Informacje o przebiegu testu

Sekcja Informacje o przebiegu testu zawiera ogólne informacje o przebiegu, w tym nazwę testu, godziny rozpoczęcia i zakończenia oraz kontroler, który uruchomił test. Ta sekcja zawiera również opcjonalny opis przebiegu dodawanego po uruchomieniu testu obciążenia.

## <a name="overall-results"></a>Wyniki ogólne

Sekcja ogólne wyniki zawiera podsumowanie wyników testu, w tym liczbę żądań na sekundę, całkowitą liczbę żądań zakończonych niepowodzeniem, średni czas odpowiedzi oraz średni czas strony.

## <a name="key-statistic-top-5-slowest-pages"></a>Kluczowe statystyki: 5 najwolniejszych stron

Sekcja najwolniejszych stron zawiera 5 najwolniejszych stron w teście obciążenia. Na każdej stronie są wyświetlane adresy URL i średni czas ładowania strony. Strony są wyświetlane w kolejności malejącej. Możesz wybrać adres URL strony, aby otworzyć tabelę **stron** i zbadać więcej szczegółów na tej stronie. Aby uzyskać więcej informacji, zobacz [How to: View Web Page Response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Wartość percentylu dla **95% czasu strony (s)** raportu, że 95% stron ukończonych w czasie krótszym niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-tests"></a>Kluczowe statystyki: 5 najwolniejszych testów

Sekcja najwolniejszych testów zawiera 5 najwolniejszych testów w teście obciążenia. Nazwa testu i średni czas testu są wyświetlane dla każdego testu. Testy są wymienione w kolejności malejącej. Możesz wybrać nazwę testu, aby otworzyć tabelę **testy** i zbadać więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Wartość percentylu dla **95% czasu testu (s)** oznacza, że 95% testów zakończyło się krócej niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Kluczowe statystyki: 5 najwolniejszych operacji SQL

Jeśli śledzenie SQL jest włączone w teście obciążenia, sekcja najwolniejszych zapytań zawiera 5 najwolniejszych zapytań w teście obciążenia. Nazwa operacji i czas trwania są wyświetlane dla każdego testu. Czas trwania jest wyświetlany w mikrosekundach (SQL Server 2005) lub milisekund (SQL Server 2000 i wcześniejszych). Testy są wymienione w kolejności malejącej według czasu trwania. Możesz wybrać nazwę operacji, aby otworzyć tabelę **śledzenia SQL** i zbadać więcej szczegółów dotyczących tej operacji. Aby uzyskać więcej informacji, zobacz [tabelę danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Wyniki testu

Sekcja wyniki testu zawiera listę wszystkich testów i scenariuszy w teście obciążenia. Nazwa testu, scenariusz, liczba uruchomień, liczba wystąpień zakończonych niepowodzeniem i średni czas testu. Możesz wybrać nazwę testu, aby otworzyć tabelę **testy** i zbadać więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="page-results"></a>Wyniki strony

Sekcja wyniki strony zawiera listę wszystkich stron sieci Web w teście obciążenia. Wyświetlany jest adres URL, scenariusz, nazwa testu, średni czas strony i liczba. Możesz wybrać adres URL strony, aby otworzyć tabelę **stron** i zbadać więcej szczegółów na tej stronie. Aby uzyskać więcej informacji, zobacz [How to: View Web Page Response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="transaction-results"></a>Wyniki transakcji

Sekcja wyniki transakcji zawiera listę wszystkich transakcji w teście obciążenia. Zostanie wyświetlona nazwa transakcji, scenariusz, test, czas odpowiedzi, czas, który upłynął i liczba. Możesz wybrać nazwę transakcji, aby otworzyć tabelę **transakcji** i zbadać więcej szczegółów dotyczących tej transakcji. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

Wartości percentylu raportują następujące informacje o transakcji:

- 90% łącznej liczby transakcji zostało ukończonych w czasie krótszym niż \<time> sekundy.

- 95% łącznej liczby transakcji zostało ukończonych w czasie krótszym niż \<time> sekundy.

## <a name="system-under-test-resources"></a>Zasoby testowe systemu

Sekcja Zasoby testowe systemu zawiera listę komputerów, które są zbiorem komputerów docelowych, dla których ładowanie jest generowane. Obejmuje każdy komputer, na którym zbierane są zestawy liczników inne niż agent lub kontroler. Zostanie wyświetlona nazwa komputera, czas procesora (%) i dostępna pamięć. Możesz wybrać nazwę komputera, aby otworzyć system na wykresie **testowym** i zobaczyć użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="controller-and-agent-resources"></a>Zasoby kontrolera i agenta

Sekcja Zasoby kontrolera i agenta zawiera listę komputerów, które są używane do uruchomienia testu. Zostanie wyświetlona nazwa komputera, czas procesora (%) i dostępna pamięć. Możesz wybrać nazwę komputera, aby otworzyć wykres **kontroler i agenci** i zobaczyć użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="errors"></a>błędy

Sekcja błędy zawiera listę wszystkich błędów, które wystąpiły podczas testu obciążenia. Zostanie wyświetlony typ i podtyp błędu, liczba i ostatni komunikat. Możesz wybrać błąd, aby otworzyć tabelę **Błędy** i zbadać więcej szczegółów dotyczących tego błędu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Możesz zwinąć i rozwinąć tę sekcję, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="print-a-summary"></a>Drukowanie podsumowania

Podsumowanie testu obciążenia można wydrukować, wybierając pozycję **Drukuj** w menu skrótów na stronie Podsumowanie. Możesz wyświetlić podgląd wydruku, wybierając pozycję **Podgląd wydruku** w menu skrótów na stronie Podsumowanie. Możesz również wydrukować bezpośrednio na ekranie podglądu.

## <a name="see-also"></a>Zobacz też

- [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
