---
title: Analizowanie naruszeń zasady progu w testach obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: be0784197c03aa3117d559cd4aa99797027c8170
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061814"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analizowanie naruszeń zasady progu w testach obciążenia za pomocą analizatora testu obciążenia

Reguły progów są skojarzone z specyficzne liczniki wydajności, a naruszenia wskazują, że licznik wydajności przekracza lub spadła poniżej wartości zestawu. Po uruchomieniu testu obciążenia, można analizować naruszeń dla reguły progów, które wcześniej.

W przypadku wszelkich naruszeniach, **naruszenia progu** hiperłącze pojawia się na **analizatora testu obciążenia** pasek stanu i określa liczbę naruszeń, które wystąpiły. Możesz wybrać hiperlink, aby wyświetlić tabelę naruszenia progu. Można również wyświetlić naruszenie progowe w **liczniki** okna, a na wykresie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Wyświetl naruszenie progowe w tabeli

 Tabeli naruszenia progu są wyświetlane pierwsze 1000 naruszenia. Poniższa tabela zawiera następujące kolumny:

|Kolumny|Opis|Domyślnie widoczny|
|-|-|-|
|Godzina|Czas podczas ładowania testu, w której nastąpiło naruszenie zasad.|Tak|
|Komputer|Nazwa komputera w ramach testu, w którym wystąpiło naruszenie. **Uwaga:** jest to istotne, kiedy uruchamiasz testy obciążenia na stanowiska.|Tak|
|Kategoria|Kategoria licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Licznik|Nazwa licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Wystąpienie|Wystąpienie licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Komunikat|Komunikat, który opisuje naruszenie progu. Na przykład **wartość 5 przekracza krytyczną wartość progową równą 0**.|Tak|

> [!NOTE]
> Możesz sortować tabeli, wybierając nagłówków kolumn.

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Wyświetl naruszenie progowe w panelu liczników

 Możesz wyświetlić naruszenie progowe w **liczniki** panelu w drzewie, zawierającego listę liczników wydajności dla testu obciążeniowego. Ikony w **liczniki** panelu komunikacji naruszenia progu. Ikona będzie jedną z następujących czynności:

 Ikona będzie jedną z następujących czynności:

 ![Nie naruszenie progu](../test/media/icon_ltest_1.gif) Nie naruszenie progu.

 ![Naruszenie progu krytycznego w ostatnim interwale](../test/media/icon_ltest_2.gif) Naruszenie progu krytycznego podczas ostatniego interwału.

 ![Naruszenie progu krytycznego na wcześniejsze interwału](../test/media/icon_ltest_3.gif) Naruszenie progu krytycznego podczas poprzedniego interwału.

 ![Naruszenie progu ostrzegawczego w ostatnim interwale](../test/media/icon_ltest_4.gif) Naruszenie progu ostrzegawczego podczas ostatniego interwału.

 ![Naruszenie progu ostrzegawczego na wcześniejsze interwału](../test/media/icon_ltest_5.gif) Naruszenie progu ostrzegawczego podczas poprzedniego interwału.

 Opcjonalnie naruszenia wartości progowych mogą być wyświetlane na wykresie, również. Ikona progu pojawia się na wykresie obok punktu danych, w którym wystąpiło naruszenie progu.

 W drzewie liczników ikona naruszenia progu są propagowane z węzła określonego licznika, aż węzeł główny. Ta ostrzega o naruszenie na licznik, który może nie być widoczna w drzewie, ponieważ nie została rozwinięta drzewa.

## <a name="view-threshold-violations-on-the-graph"></a>Wyświetl naruszenia progowe na wykresie

 Możesz wyświetlić naruszenia progowe na wykresie. Podobnie jak **liczniki** panelu ikony komunikacji naruszenia progowe na wykresie. Ikony są wyświetlane na wykresie obok punktu danych, w którym wystąpiło naruszenie progu. W przypadku naruszenia progu na licznik, który nie jest wyświetlana na wykresie, można dodać go do wykresu, przeciągając go z **liczniki** panelu do wykresu.

 Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)