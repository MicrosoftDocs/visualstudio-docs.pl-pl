---
title: Dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 079a7390b462dd8d48535f683f391ec2dca4827d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916799"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Instrukcje: Dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia

Możesz użyć **liczniki** panelu, aby dodać liczniki wydajności do wykresu.

![Dodano liczników do wykresu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Zagadnienia interwału próbkowania licznika wydajności**

Wybierz wartość dla **częstotliwość próbkowania** uruchomieniowe właściwości w teście obciążenia, na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, np. wartość domyślna pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dla dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [jak: Określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Oto niektóre wytyczne dotyczące częstotliwości próbkowania:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\< 1 godzina|5 sekund|
|1 - 8 godzin|15 sekund|
|8 - 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

**Zagadnienia dotyczące szczegółowych informacji o czasie do zbierania danych percentyl, w tym**

Jest właściwością w ustawieniach uruchamiania w edytorze testu obciążenia o nazwie **przechowywanie informacji**. Jeśli **przechowywanie informacji** właściwość jest włączona, a następnie to czas na wykonanie każdego indywidualnego testu, transakcji i strony podczas testu obciążenia, które będą przechowywane w repozytorium wyników testu obciążenia. Umożliwia to 90 i 95. percentyl danych w **analizatora testu obciążenia** w tabelach testy, transakcji i strony.

Istnieją dwie możliwości włączenia **przechowywanie informacji** właściwość we właściwościach parametrów uruchomieniowych o nazwie **StatisticsOnly** i **AllIndividualDetails**. Niezależnie od wybranej opcji wszystkie poszczególne testy, strony i transakcje są upłynął limit czasu i percentyli są obliczane na podstawie danych o poszczególnych chronometrażach. Różnica polega na tym, wraz z **StatisticsOnly** opcji tak szybko, jak została obliczona danych percentyl, o poszczególnych chronometrażach, dane są usuwane z repozytorium. Zmniejsza to ilość miejsca wymaganego w repozytorium, użyj szczegółów chronometrażu. Jednak użytkownicy zaawansowani może być do przetwarzania danych szczegółów chronometrażu w inny sposób, przy użyciu narzędzi SQL. Jeśli tak, jest **AllIndividualDetails** tak, aby dane szczegółowe chronometrażu były dostępne dla tego przetwarzania, należy użyć opcji. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, następnie można analizować aktywności wirtualnego użytkownika za pomocą **wirtualnego aktywności użytkownika** wykresu w **analizatora testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizować aktywność wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania szczegółowych danych o chronometrażu mogą być bardzo duże, szczególnie w przypadku uruchamiania dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testów obciążeniowych na koniec testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testowych obciążenia do momentu zakończenia testów obciążenia. Po zakończeniu testu obciążenia, dane są przechowywane w repozytorium. Domyślnie **przechowywanie informacji** właściwość jest włączona. Jeśli jest to problem dla środowiska testowego, warto ustawić **przechowywanie informacji** do **Brak**.

Aby uzyskać więcej informacji, zobacz [jak: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Aby wyświetlić konkretnego licznika wydajności na wykresie testu obciążenia

1.  Po zakończeniu testu obciążeniowego lub po załadowaniu wynik testu na pasku narzędzi analizatora testu obciążeniowego wybierz **wykresów**.

     **Liczniki** panel jest wyświetlany w widoku wykresu.

    > [!NOTE]
    > Jeśli **liczniki** panel nie jest widoczny, wybierz polecenie **Pokaż Panel liczników** na pasku narzędzi.

2.  W **liczniki** panelu, rozwiń węzły w hierarchii, dopóki nie znajdziesz licznika wydajności, który ma zostać wyświetlone w formie graficznej.

     Na przykład, aby wyświetlić ilość dostępnej pamięci na komputerze, na którym uruchomiono testy, rozwiń węzeł **komputerów**, rozwiń węzeł komputera, a następnie rozwiń **pamięci**. Zostanie wyświetlony **dostępnej ilości megabajtów** licznika.

3.  Wybierz wykres, na którym chcesz wyświetlić licznika wydajności.

4.  Kliknij prawym przyciskiem myszy licznik wydajności w **liczniki** panelu, a następnie wybierz pozycję **Pokaż licznik na wykresie**.

    > [!TIP]
    > Aby tymczasowo zatrzymać wyświetlanie danych licznika wydajności na wykresie, wyczyść pole wyboru dla licznika wydajności w legendzie. Dzięki temu statystyki minimalna, maksymalna i średnia, które mają być analizowane bez wyświetlania linię trendu na wykresie. Może to być przydatne, jeśli wykres zawiera kilka nakładających się wykresy liczników wydajności podczas analizowania problemów. Aby uzyskać więcej informacji, zobacz [analizowanie testów obciążenia przy użyciu legendy wykresu](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Aby usunąć dane licznika wydajności z wykresu, kliknij prawym przyciskiem myszy licznik wydajności w **licznika** kolumny legendy, a następnie wybierz pozycję **Usuń**.

     \- lub —

     Kliknij prawym przyciskiem myszy wiersza danych w wykres i wybierz pozycję **Usuń**.

     \- lub —

     Wybierz licznik wydajności w **licznika** kolumny legendy lub dane linii na wykresie, a następnie naciśnij klawisz **Usuń** klucza.

    > [!NOTE]
    > Możesz również umieścić w legendzie, ale nie na wykresie licznika wydajności przy użyciu **Dodaj licznik w legendzie** polecenia.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)