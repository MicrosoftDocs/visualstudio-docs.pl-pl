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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3f5187aabeb0c8e2ef81b0c6b6883b96590d7005
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062612"
---
# <a name="load-test-results-summary-overview"></a>Przegląd podsumowania wyników testu obciążenia

Po uruchomieniu testu obciążenia, możesz wyświetlić podsumowanie testu obciążeniowego, aby szybko poznać wyniki. Podsumowanie testu obciążeniowego zapewnia kluczowe wyniki w compact, łatwe do odczytania formacie. Pozwala również na drukowanie podsumowania testu obciążenia. Ułatwia to używane podczas komunikowania się wyniki do zainteresowanych stron. Podsumowanie testu obciążeniowego jest również domyślny widok, po otwarciu wyniku testu obciążeniowego z wcześniej uruchomionego testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [porady: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

![Widok podsumowania](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Podsumowanie testu obciążeniowego

Podsumowanie testu obciążeniowego jest podzielona na sekcje. Początkowe sekcje są wyświetlane u góry strony podsumowania i są zawsze widoczne. Podczas wyświetlania podsumowania testu obciążenia pierwszego są następujące elementy:

- Informacje o przebiegu testu

- Ogólne wyniki

- Kluczowe statystyki: 5 najpopularniejszych najwolniejszych stron

- Kluczowe statystyki: Top 5 najwolniejszych testów

- Kluczowe statystyki: Top 5 najwolniejszych operacji SQL

    > [!NOTE]
    > W sekcji operacji SQL jest wyświetlana tylko wtedy, gdy włączone jest śledzenie SQL w teście obciążeniowym.

Sekcje zamknięcia pojawiają się pod koniec podsumowania i może zostać zwinięty, aby zaoszczędzić miejsce. Na koniec podsumowania testu obciążenia wyświetlane są następujące elementy:

- Wyniki tekstu

- Wyniki strony

- Wyniki transakcji

- System w trakcie zasobów testowych

- Kontroler i Agent zasobów

- błędy

## <a name="test-run-information"></a>Informacje o przebiegu testu

Sekcja informacji o przebiegu testu zawiera ogólne informacje o przebiegu, łącznie z nazwą testu, rozpoczęcia i zakończenia oraz kontroler, który prowadził test. Ta sekcja zawiera również opcjonalny opis przebiegu, możesz dodać po uruchomieniu testu obciążenia.

## <a name="overall-results"></a>Ogólne wyniki

Ogólny sekcja wyników zawiera podsumowania wyników testu, w tym liczbę żądań na sekundę, całkowita liczba żądań zakończonych niepowodzeniem, Średni czas odpowiedzi i czas średni strony.

## <a name="key-statistic-top-5-slowest-pages"></a>Kluczowe statystyki: 5 najwolniejszych stron

Sekcji Najwolniejsze strony zawiera 5 pierwszych Najwolniejsze strony w teście obciążeniowym. Adres URL i czas ładowania strony są wyświetlane dla każdej strony. Strony są wymienione w kolejności malejącej. Możesz wybrać adres URL strony, aby otworzyć **stron** tabeli i sprawdzić szczegółowe informacje dla tej strony. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie odpowiedzi strony web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Wartość percentylu **95% czasu strony (s)** zgłosić, że 95% strony ma być wykonane w czasie krótszym niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-tests"></a>Kluczowe statystyki: 5 najwolniejszych testów

Najwolniejsze sekcja testów zawiera najważniejsze 5 najwolniejszych testów w teście obciążeniowym. Nazwa testu i Średni czas testu są wyświetlane dla każdego testu. Testy są wymienione w kolejności malejącej. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i sprawdzić szczegółowe informacje dla tego testu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Wartość percentylu **95% czasu testu (s)** zgłosić, że 95% testy wykonane w czasie krótszym niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Kluczowe statystyki: 5 najwolniejszych operacji SQL Top

Włączenie śledzenia SQL w teście obciążeniowym najwolniejsze sekcja zapytań zawiera najpopularniejsze 5 najwolniejszych zapytania w teście obciążeniowym. Nazwa operacji i czas trwania są wyświetlane dla każdego testu. Czas trwania jest wyświetlany w mikrosekundach (SQL Server 2005) lub milisekund (SQL Server 2000 lub starszym). Testy są wymienione w kolejności malejącej według czasu trwania. Można wybrać nazwę działania, aby otworzyć **śledzenia SQL** tabeli i sprawdzić szczegółowe informacje dla tej operacji. Aby uzyskać więcej informacji, zobacz [tabeli danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Wyniki testu

Sekcja wyniki testu zawiera listę wszystkich testów i scenariusze do testu obciążeniowego. Nazwa testu, scenariusz, ile razy został uruchomiony, ile razy nie powiodło się oraz średni czas testu są wyświetlane. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i sprawdzić szczegółowe informacje dla tego testu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

## <a name="page-results"></a>Wyniki strony

Sekcja wyniki strona zawiera listę wszystkich stron sieci web w teście obciążeniowym. Adres URL, scenariusz, nazwy testu, czas strony średni i liczby są wyświetlane. Możesz wybrać adres URL strony, aby otworzyć **stron** tabeli i sprawdzić szczegółowe informacje dla tej strony. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie odpowiedzi strony web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

## <a name="transaction-results"></a>Wyniki transakcji

Sekcja wyniki transakcji zawiera listę wszystkich transakcji w teście obciążeniowym. Nazwa transakcji, scenariusz, testu, czas odpowiedzi, upłynęło czasu i liczby są wyświetlane. Można wybrać nazwę transakcji, aby otworzyć **transakcji** tabeli i sprawdzić szczegółowe informacje dla tej transakcji. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

Wartości percentyla raportu następujące informacje o transakcji:

-   Zakończono 90% łącznej liczby transakcji w mniej niż \<czas > sekund.

-   Zakończono 95% łącznej liczby transakcji w mniej niż \<czas > sekund.

## <a name="system-under-test-resources"></a>System w trakcie zasobów testowych

System sekcji Zasoby testu zawiera listę komputerów, które są zbiór komputerów docelowych, dla których obciążenie jest generowane. Dotyczy to również dowolnego komputera, z którego są zbierane zbiory liczników, innym niż agenta lub kontrolera. Nazwa komputera, % czasu procesora i pamięci są wyświetlane. Można wybrać nazwę komputera, aby otworzyć **badanego** programu graph i sprawdź wykorzystanie zasobów wraz z upływem czasu. Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

## <a name="controller-and-agent-resources"></a>Zasoby kontrolera i agenta

Sekcja Zasoby kontrolera i agenta zawiera listę komputerów, które są używane do uruchomienia testu. Nazwa komputera, % czasu procesora i pamięci są wyświetlane. Można wybrać nazwę komputera, aby otworzyć **kontrolera i agentów** programu graph i sprawdź wykorzystanie zasobów wraz z upływem czasu. Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

## <a name="errors"></a>błędy

Sekcja błędów zawiera listę wszystkich błędów, które wystąpiły podczas testu obciążeniowego. Typ i podtyp błąd, liczby wartości oraz ostatni komunikat są wyświetlane. Możesz wybrać błędu, aby otworzyć **błędy** tabeli i Sprawdź więcej szczegółów tego błędu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Można zwinąć, a następnie rozwiń tę sekcję, wybierając strzałkę po lewej stronie w tytułach sekcji.

## <a name="print-a-summary"></a>Drukowanie podsumowania

Podsumowanie testu obciążeniowego można wydrukować, wybierając **drukowanie** menu skrótów w podsumowaniu. Możesz wyświetlić podgląd wydruku pierwszy, wybierając **Podgląd wydruku** menu skrótów w podsumowaniu. Można również drukować bezpośrednio z ekranu (wersja zapoznawcza).

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)