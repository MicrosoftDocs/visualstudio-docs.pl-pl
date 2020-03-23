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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584494"
---
# <a name="load-test-results-summary-overview"></a>Podsumowanie wyników testu obciążenia

Po uruchomieniu testu obciążenia można wyświetlić podsumowanie testu obciążenia, aby szybko zrozumieć wyniki. Podsumowanie testu obciążenia zawiera kluczowe wyniki w kompaktowym i łatwym do odczytania formacie. Można również wydrukować podsumowanie testu obciążenia. Dzięki temu jest wygodny w użyciu podczas przekazywania wyników do zainteresowanych stron. Podsumowanie testu obciążenia jest również widokiem domyślnym po otwarciu wyniku testu obciążenia z wcześniej uruchomionego testu obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

![Widok podsumowania](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Podsumowanie testu obciążenia

Podsumowanie testu obciążenia jest podzielone na sekcje. Początkowe sekcje są wyświetlane w górnej części podsumowania i są zawsze widoczne. Podczas wyświetlania podsumowania testu obciążenia najpierw są następujące elementy:

- Informacje o przebiegu testu

- Ogólne wyniki

- Kluczowa statystyka: 5 najwolniejszych stron

- Kluczowa statystyka: 5 najwolniejszych testów

- Statystyka klucza: Top 5 najwolniejszych operacji SQL

    > [!NOTE]
    > Sekcja Operacje SQL jest wyświetlana tylko wtedy, gdy śledzenie SQL jest włączone w teście obciążenia.

Sekcje zamykające są wyświetlane na końcu podsumowania i mogą być zwinięte, aby zaoszczędzić miejsce. Na końcu podsumowania testu obciążenia pojawiają się następujące elementy:

- Wyniki tekstu

- Wyniki strony

- Wyniki transakcji

- Zasoby testowe systemu

- Zasoby kontrolera i agenta

- Errors

## <a name="test-run-information"></a>Informacje o przebiegu testu

Sekcja informacji o przebiegu testu zawiera ogólne informacje o przebiegu, w tym nazwę testu, godziny rozpoczęcia i zakończenia oraz kontroler, który uruchomił test. Ta sekcja zawiera również opcjonalny opis uruchomienia, który można dodać po uruchomieniu testu obciążenia.

## <a name="overall-results"></a>Ogólne wyniki

Ogólna sekcja wyników zawiera wyniki podsumowania testu, w tym liczbę żądań na sekundę, całkowitą liczbę żądań, które nie powiodły się, średni czas odpowiedzi i średni czas strony.

## <a name="key-statistic-top-5-slowest-pages"></a>Kluczowa statystyka: 5 najwolniejszych stron

Sekcja najwolniejszych stron zawiera 5 najwolniejszych stron w teście obciążenia. Adres URL i średni czas wczytynia strony są wyświetlane dla każdej strony. Strony są wyświetlane w porządku malejącym. Możesz wybrać adres URL strony, aby otworzyć tabelę **Strony** i sprawdzić więcej szczegółów dla tej strony. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie odpowiedzi na stronę internetową](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Wartość percentyla dla **95% czasu strony (s)** raport, że 95% stron ukończone w mniej niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-tests"></a>Kluczowa statystyka: 5 najwolniejszych testów

Sekcja najwolniejszych testów zawiera 5 najwolniejszych testów w teście obciążenia. Nazwa testu i średni czas testowania są wyświetlane dla każdego testu. Testy są wymienione w porządku malejącym. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i sprawdzić więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Wartość percentyla dla **95% czasu testu (s)** raport, że 95% testów zakończone w mniej niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Kluczowa statystyka: 5 najwolniejszych operacji SQL

Jeśli śledzenie SQL jest włączone w teście obciążenia, najwolniejsze kwerendy sekcja zawiera 5 najbardziej nawolniejszych zapytań w teście obciążenia. Nazwa operacji i czas trwania są wyświetlane dla każdego testu. Czas trwania jest wyświetlany w mikrosekundach (SQL Server 2005) lub milisekundach (SQL Server 2000 i wcześniejszych). Testy są wyświetlane w kolejności malejącej według czasu trwania. Można wybrać nazwę operacji, aby otworzyć tabelę **śledzenia SQL** i sprawdzić więcej szczegółów dla tej operacji. Aby uzyskać więcej informacji, zobacz [tabela danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Wyniki testu

Sekcja wyników testów zawiera listę wszystkich testów i scenariuszy w teście obciążenia. Nazwa testu, scenariusz, liczba uruchomionych uruchomiono, ile razy nie powiodło się i średni czas testu są wyświetlane. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i sprawdzić więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="page-results"></a>Wyniki strony

Sekcja wyników strony zawiera listę wszystkich stron internetowych w teście obciążenia. Wyświetlany jest adres URL, scenariusz, nazwa testu, średni czas strony i liczba. Możesz wybrać adres URL strony, aby otworzyć tabelę **Strony** i sprawdzić więcej szczegółów dla tej strony. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie odpowiedzi na stronę internetową](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="transaction-results"></a>Wyniki transakcji

Sekcja wyniki transakcji zawiera listę wszystkich transakcji w teście obciążenia. Wyświetlana jest nazwa transakcji, scenariusz, test, czas odpowiedzi, czas, jaki upłynął i liczba. Można wybrać nazwę transakcji, aby otworzyć tabelę **Transakcje** i sprawdzić więcej szczegółów dla tej transakcji. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

Wartości percentylu zgłaszają następujące informacje o transakcji:

- 90% wszystkich transakcji zostało zrealizowanych \<w czasie krótszym niż> sekund.

- 95% wszystkich transakcji zostało zrealizowanych \<w czasie krótszym niż> sekund.

## <a name="system-under-test-resources"></a>System w zasobach testowych

Sekcja zasobów testowych systemu zawiera listę komputerów, które są zestawem komputerów docelowych, dla których generowane jest ładowanie. Obejmuje to każdy komputer, z którego zbierane są zestawy liczników inne niż agent lub kontroler. Wyświetlana jest nazwa komputera, % czasu procesora i dostępna pamięć. Można wybrać nazwę komputera, aby otworzyć system w obszarze Wykres **testowy** i zobaczyć użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="controller-and-agent-resources"></a>Zasoby kontrolera i agenta

Sekcja zasobów kontrolera i agenta zawiera listę komputerów, które są używane do uruchomienia testu. Wyświetlana jest nazwa komputera, % czasu procesora i dostępna pamięć. Można wybrać nazwę komputera, aby otworzyć wykres **Kontroler i agenci** i wyświetlić użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="errors"></a>Errors

Sekcja błędy zawiera listę wszystkich błędów, które wystąpiły podczas testu obciążenia. Wyświetlany jest typ i podtyp błędu, liczba i ostatni komunikat. Można wybrać błąd, aby otworzyć tabelę **Błędy** i sprawdzić więcej szczegółów dla tego błędu. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tę sekcję można zwinąć i rozwinąć, wybierając strzałkę po lewej stronie tytułu sekcji.

## <a name="print-a-summary"></a>Drukowanie podsumowania

Podsumowanie testu obciążenia można wydrukować, wybierając **pozycję Drukuj** w menu skrótów w podsumowaniu. Wydruk można wyświetlić najpierw, wybierając **pozycję Podgląd wydruku** w menu skrótów w podsumowaniu. Można również drukować bezpośrednio z ekranu podglądu.

## <a name="see-also"></a>Zobacz też

- [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
