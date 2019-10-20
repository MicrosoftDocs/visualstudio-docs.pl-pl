---
title: Dodawanie i usuwanie liczników na wykresach w Wyniki testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b589e45fe32aff1ce0eea338675d42c3e3ea944a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644360"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Porady: dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia

Aby dodać liczniki wydajności do grafu, można użyć panelu **liczników** .

![Dodano licznik do grafu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Zagadnienia dotyczące interwału próbkowania licznika wydajności**

Wybierz wartość właściwości **częstotliwość próbkowania** w ustawieniach przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie szybkości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [How to: określ częstotliwość próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono niektóre wskazówki dotyczące stawek próbek:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\< 1 godz.|5 sekund|
|1-8 godzin|15 sekund|
|8-24 godzin|30 sekund|
|> 24 godziny|60 sekund|

**Zagadnienia dotyczące wyświetlania szczegółowych informacji o czasie w celu zbierania danych percentylu**

Istnieje właściwość w ustawieniach uruchomieniowych w Edytor testu obciążeniowego nazwanego **magazynu informacji o chronometrażu**. Jeśli właściwość **przechowywanie informacji** o czasie jest włączona, czas wykonywania poszczególnych testów, transakcji i stron podczas testu obciążenia będzie przechowywany w repozytorium wyników testu obciążenia. Pozwala to na wyświetlanie 90 i używany 95. percentylu danych w **analizatorze testu obciążenia** w tabelach testów, transakcji i stron.

Dostępne są dwie opcje włączenia właściwości **przechowywanie informacji o chronometrażu** we właściwościach parametrów uruchomieniowych o nazwach **StatisticsOnly** i **AllIndividualDetails**. W przypadku każdej opcji wszystkie poszczególne testy, strony i transakcje są czasowe, a dane percentylu są obliczane na podstawie poszczególnych danych o chronometrażu. Różnica polega na tym, że z opcją **StatisticsOnly** , gdy tylko dane percentylu zostały obliczone, dane o poszczególnych chronometrażach są usuwane z repozytorium. Zmniejsza to ilość miejsca wymaganego w repozytorium podczas korzystania ze szczegółowych informacji o chronometrażu. Jednak zaawansowani użytkownicy mogą chcieć przetwarzać dane szczegółowe o chronometrażu w inny sposób, korzystając z narzędzi SQL. W takim przypadku należy użyć opcji **AllIndividualDetails** , aby dane szczegółowe dotyczące chronometrażu były dostępne dla tego przetwarzania. Ponadto, jeśli właściwość zostanie ustawiona na **AllIndividualDetails**, można analizować aktywność wirtualnego użytkownika za pomocą wykresu **aktywności wirtualnego użytkownika** w **analizatorze testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania danych szczegółów chronometrażu może być bardzo duża, szczególnie w przypadku dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testu obciążenia na końcu testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testów obciążenia do momentu zakończenia testu obciążenia. Po zakończeniu testu obciążenia dane są przechowywane w repozytorium. Domyślnie właściwość **przechowywanie informacji** o czasie jest włączona. Jeśli jest to problem dla środowiska testowego, można ustawić **przechowywanie informacji o chronometrażu** na **Brak**.

Aby uzyskać więcej informacji, zobacz [How to: Określ właściwość Storage Details](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Aby wyświetlić określony licznik wydajności na wykresie testu obciążenia

1. Po zakończeniu testu obciążenia lub po załadowaniu wyniku testu na pasku narzędzi analizatora testu obciążenia wybierz **Wykres**.

     Panel **liczniki** zostanie wyświetlony w widoku wykresy.

    > [!NOTE]
    > Jeśli panel **liczniki** nie jest widoczny, wybierz pozycję **Pokaż panel liczników** na pasku narzędzi.

2. W panelu **liczniki** rozwiń węzeł węzły w hierarchii do momentu znalezienia licznika wydajności, który ma być wyświetlany graficznie.

     Aby na przykład wyświetlić dostępną pamięć na komputerze, na którym są uruchomione testy, rozwiń węzeł **komputery**, rozwiń węzeł komputera, a następnie rozwiń węzeł **pamięć**. Zostanie wyświetlony licznik **dostępne MB** .

3. Wybierz wykres, na którym chcesz wyświetlić licznik wydajności.

4. Kliknij prawym przyciskiem myszy licznik wydajności w panelu **liczniki** i wybierz polecenie **Pokaż licznik na grafie**.

    > [!TIP]
    > Aby tymczasowo zatrzymać wyświetlanie danych licznika wydajności na wykresie, usuń zaznaczenie pola wyboru dla licznika wydajności w legendzie. Dzięki temu minimalna, maksymalna i średnia Statystyka nadal będzie analizowana bez wyświetlania linii trendu na grafie. Może to być przydatne, jeśli wykres zawiera kilka nakładających się wykresów liczników wydajności podczas analizowania problemów. Aby uzyskać więcej informacji, zobacz [Używanie legendy widoku wykresy do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Aby usunąć dane licznika wydajności z grafu, kliknij prawym przyciskiem myszy licznik wydajności w kolumnie **licznik** legendy i wybierz polecenie **Usuń**.

     \- lub-

     Kliknij prawym przyciskiem myszy wiersz danych na grafie i wybierz polecenie **Usuń**.

     \- lub-

     Wybierz licznik wydajności w kolumnie **licznik** legendy lub wiersz danych na grafie, a następnie naciśnij klawisz **delete** .

    > [!NOTE]
    > Można również umieścić licznik wydajności w legendzie, ale nie na grafie, za pomocą polecenia **Dodaj licznik w legendzie** .

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)