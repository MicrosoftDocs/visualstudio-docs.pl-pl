---
title: Dodawanie i usuwanie liczników na wykresach w wynikach testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acb08edf74d3ca35a2449f588976681d679caeb4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115180"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Porady: dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia

Za pomocą panelu **Liczniki** można dodawać liczniki wydajności do wykresu.

![Dodano licznik do wykresu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Zagadnienia interwału próbkowania licznika wydajności**

Wybierz wartość dla **sample rate** właściwości w ustawieniach przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak wartość domyślna wynosząca pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [Jak: Określanie częstotliwości próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Oto kilka wskazówek dotyczących przykładowych stawek:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\<1 godz.|5 sekund|
|1 - 8 godzin|15 sekund|
|8 - 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

**Zagadnienia dotyczące dołączania szczegółów chronometrażu do zbierania danych percentylowych**

Istnieje właściwość w ustawieniach uruchamiania w Edytorze testu obciążenia o nazwie **Magazyn szczegółów chronometrażu**. Jeśli właściwość **magazyn szczegółów chronometrażu** jest włączona, czas wykonania każdego testu, transakcji i strony podczas testu obciążenia będzie przechowywany w repozytorium wyników testu obciążenia. Dzięki temu 90 i 95 percentyl danych, które mają być wyświetlane w **analizatorze testu obciążenia** w testach, transakcji i stron tabel.

Istnieją dwie opcje włączania właściwości **Magazyn szczegółów chronometrażu** we właściwościach ustawień uruchamiania o nazwie **StatisticsOnly** i **AllIndividualDetails**. W obu przypadkach wszystkie poszczególne testy, strony i transakcje są czasowe, a dane percentyla są obliczane na podstawie poszczególnych danych chronometrażu. Różnica polega na tym, że z **StatisticsOnly** opcji, jak tylko dane percentyla został obliczony, poszczególne dane chronometrażu są usuwane z repozytorium. Zmniejsza to ilość miejsca, która jest wymagana w repozytorium podczas korzystania ze szczegółów chronometrażu. Jednak zaawansowani użytkownicy mogą chcieć przetwarzać dane szczegółów chronometrażu w inny sposób, za pomocą narzędzi SQL. W takim przypadku **allindividualDetails** opcja powinna być używana tak, aby dane szczegółów czasu jest dostępna dla tego przetwarzania. Ponadto jeśli ustawisz właściwość na **AllIndividualDetails**, następnie można analizować działanie użytkownika wirtualnego przy użyciu **wykresu aktywności użytkownika wirtualnego** w **analizatorze testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca, która jest wymagana w repozytorium wyników testu obciążenia do przechowywania danych szczegółów chronometrażu może być bardzo duża, szczególnie w przypadku dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testu obciążenia na końcu testu obciążenia jest dłuższy, ponieważ te dane są przechowywane na agentach testu obciążenia, dopóki test obciążenia nie zakończy wykonywania. Po zakończeniu testu obciążenia dane są przechowywane w repozytorium. Domyślnie włączono właściwość Magazyn szczegółów chronometrażu. **Timing Details Storage** Jeśli jest to problem dla środowiska testowego, można ustawić **magazyn szczegółów chronometrażu** na **Brak**.

Aby uzyskać więcej informacji, zobacz [Jak: Określanie właściwości magazynu szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Aby wyświetlić określony licznik wydajności na wykresie testu obciążenia

1. Po zakończeniu testu obciążenia lub po załadowaniu wyniku testu na pasku narzędzi analizatora testów obciążenia wybierz opcję **Wykresy**.

     Panel **Liczniki** jest wyświetlany w widoku Wykresy.

    > [!NOTE]
    > Jeśli panel **Liczniki** nie jest widoczny, na pasku narzędzi wybierz pozycję **Pokaż panel liczników.**

2. W panelu **Liczniki** rozwiń węzły w hierarchii, aż znajdziesz licznik wydajności, który ma być wyświetlany graficznie.

     Na przykład, aby wyświetlić dostępną pamięć na komputerze, na którym są uruchomione testy, rozwiń węzeł **Komputery**, rozwiń węzeł komputera, a następnie rozwiń **pozycję Pamięć**. Zostanie wyświetlony licznik **Dostępne bajty.**

3. Wybierz wykres, na którym ma być wyświetlany licznik wydajności.

4. Kliknij prawym przyciskiem myszy licznik wydajności w panelu **Liczniki** i wybierz polecenie **Pokaż licznik na wykresie**.

    > [!TIP]
    > Aby tymczasowo zatrzymać wyświetlanie danych licznika wydajności na wykresie, wyczyść pole wyboru licznika wydajności w legendzie. Dzięki temu statystyki min, max i średniej mogą być nadal analizowane bez wyświetlania linii trendu na wykresie. Może to być przydatne, jeśli wykres zawiera kilka nakładających się wykresów licznika wydajności podczas analizowania problemów. Aby uzyskać więcej informacji, zobacz [Używanie legendy widoku Wykresy do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Aby usunąć dane licznika wydajności z wykresu, kliknij prawym przyciskiem myszy licznik wydajności w kolumnie **Licznik** legendy i wybierz polecenie **Usuń**.

     \-lub -

     Kliknij prawym przyciskiem myszy linię danych na wykresie i wybierz polecenie **Usuń**.

     \-lub -

     Wybierz licznik wydajności w kolumnie **Licznik** legendy lub linii danych na wykresie, a następnie naciśnij klawisz **Delete.**

    > [!NOTE]
    > Można również umieścić licznik wydajności na legendzie, ale nie na wykresie za pomocą polecenia **Dodaj licznik na legendę.**

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Jak: Tworzenie niestandardowych wykresów](../test/how-to-create-custom-graphs-in-load-test-results.md)
