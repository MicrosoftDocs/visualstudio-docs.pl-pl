---
title: Analizowanie naruszeń reguły progowej w testach obciążenia
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a20c5e3f30a6d006175e78fc70dab79d0b9bf8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591284"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analizowanie naruszeń reguły progowej w testach obciążenia przy użyciu analizatora testów obciążenia

Reguły progowe są skojarzone z określonymi licznikami wydajności, a naruszenia wskazują, że licznik wydajności przekroczył lub spadł poniżej ustawionej wartości. Po uruchomieniu testu obciążenia, można analizować naruszenia, które występują dla reguł progowych, które zostały skonfigurowane wcześniej.

Jeśli wystąpiło jakiekolwiek naruszenia, **hiperłącze naruszenia progu** pojawia się na pasku stanu **analizatora testów obciążenia** i określa liczbę naruszeń, które wystąpiły. Wybierz hiperłącze, aby wyświetlić tabelę naruszeń progu. Można również wyświetlić naruszenia progów w oknie **Liczniki** i na wykresie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Wyświetlanie naruszeń progu w tabeli

W tabeli naruszeń progu wyświetlane są pierwsze 1000 naruszeń. Poniższa tabela zawiera następujące kolumny:

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|Time|Czas podczas testu obciążenia, w którym wystąpiło naruszenie.|Tak|
|Computer (Komputer)|Nazwa komputera w fazie testów, na którym wystąpiło naruszenie. **Uwaga:**  Jest to ważne podczas uruchamiania testów obciążenia na platformach.|Tak|
|Kategoria|Kategoria licznika wydajności, na którym wystąpiło naruszenie.|Tak|
|Licznik|Nazwa licznika wydajności, na którym wystąpiło naruszenie.|Tak|
|Wystąpienie|Wystąpienie licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Komunikat|Komunikat opisujący naruszenie progu. Na przykład **wartość 5 przekracza wartość progu krytycznego 0**.|Tak|

> [!NOTE]
> Tabelę można sortować, wybierając nagłówki kolumn.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Wyświetlanie naruszeń progów w panelu Liczniki

Można wyświetlić naruszenia progu w **panelu Liczniki,** w drzewie, które wyświetla liczniki wydajności dla testu obciążenia. Ikony w panelu Liczniki komunikują naruszenia **progów.** Ikona będzie jedną z następujących czynności:

Ikona będzie jedną z następujących czynności:

![Brak naruszenia progu](../test/media/icon_ltest_1.gif) Bez naruszenia progu.

![Naruszenie progu krytycznego w ostatnim interwale](../test/media/icon_ltest_2.gif) Naruszenie progu krytycznego wystąpiło w ostatnim interwale.

![Naruszenie progu krytycznego w poprzednim interwale](../test/media/icon_ltest_3.gif) Naruszenie progu krytycznego wystąpiło w poprzednim interwale.

![Naruszenie progu ostrzegawczego w ostatnim interwale](../test/media/icon_ltest_4.gif) Naruszenie progu ostrzeżenia wystąpiło w ostatnim interwale.

![Naruszenie progu ostrzegawczego w poprzednim interwale](../test/media/icon_ltest_5.gif) Naruszenie progu ostrzegawczego wystąpiło w poprzednim interwale.

Opcjonalnie naruszenia progu mogą być wyświetlane na wykresie również. Ikona progu pojawia się na wykresie obok punktu danych, w którym wystąpiło naruszenie progu.

W drzewie liczników ikona naruszenia progu jest propagowana z określonego węzła licznika, aż do węzła głównego. To ostrzega o naruszeniu na liczniku, który może nie być widoczny w drzewie, ponieważ drzewo nie zostało rozwinięte.

## <a name="view-threshold-violations-on-the-graph"></a>Wyświetlanie naruszeń progu na wykresie

Na wykresie można wyświetlić naruszenia progów. Podobnie jak w panelu **Liczniki,** ikony komunikują naruszenia progów na wykresie. Ikony są wyświetlane na wykresie obok punktu danych, w którym wystąpiło naruszenie progu. Jeśli naruszenie progu występuje na liczniku, który nie pojawia się na wykresie, można dodać go do wykresu, przeciągając go z panelu **Liczniki** do wykresu.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz też

- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
