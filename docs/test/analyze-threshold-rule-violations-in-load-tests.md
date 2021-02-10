---
title: Analizowanie naruszeń reguł progu w testach obciążenia
description: Dowiedz się, jak wyświetlać naruszenia reguł progowych, które zostały skonfigurowane, aby można było analizować naruszenia.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 519a908b85c6cdf3dbecc38e032d72ac223a8bdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948052"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analizowanie naruszeń reguł progu w testach obciążenia za pomocą analizatora testu obciążenia

Reguły progów są skojarzone z konkretnymi licznikami wydajności, a naruszenia wskazują, że licznik wydajności został przekroczony lub spadł poniżej wartości ustawionej. Po uruchomieniu testu obciążenia można analizować naruszenia, które następują dla reguł progu, które zostały wcześniej skonfigurowane.

Jeśli wystąpią jakieś naruszenia, na pasku stanu **analizatora testu obciążenia** pojawia się hiperłącze **naruszenia progu** i określa liczbę naruszeń, które wystąpiły. Wybierz hiperlink, aby wyświetlić tabelę naruszeń progu. Możesz również wyświetlić naruszenia progu w oknie **liczniki** i na grafie.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Wyświetl naruszenia progu w tabeli

W tabeli naruszeń progowych są wyświetlane pierwsze naruszenia 1 000. Poniższa tabela zawiera następujące kolumny:

|Kolumna|Opis|Domyślnie widoczne|
|-|-|-|
|Godzina|Czas podczas testu obciążenia, w którym wystąpiło naruszenie.|Tak|
|Computer (Komputer)|Nazwa testowanego komputera, na którym wystąpiło naruszenie. **Uwaga:**  Jest to ważne w przypadku uruchamiania testów obciążenia w ramach platform.|Tak|
|Kategoria|Kategoria licznika wydajności, na którym wystąpiło naruszenie.|Tak|
|Licznik|Nazwa licznika wydajności, na którym wystąpiło naruszenie.|Tak|
|Wystąpienie|Wystąpienie licznika wydajności, na którym wystąpiło naruszenie.|Tak|
|Komunikat|Komunikat opisujący naruszenie progu. Na przykład **wartość 5 przekracza krytyczną wartość progową 0**.|Tak|

> [!NOTE]
> Tabelę można sortować, wybierając nagłówki kolumn.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Wyświetlanie naruszeń progu w panelu liczniki

Naruszenia progu można wyświetlić w panelu **liczniki** w drzewie, w którym są wyświetlane liczniki wydajności dla testu obciążenia. Ikony w panelu **liczniki** komunikują się naruszeniami progowymi. Ikona będzie mieć jedną z następujących wartości:

Ikona będzie mieć jedną z następujących wartości:

![Brak naruszenia progu](../test/media/icon_ltest_1.gif) Brak naruszenia progu.

![Krytyczne naruszenie progu dla ostatniego interwału](../test/media/icon_ltest_2.gif) W ostatnim interwale wystąpiło naruszenie progu krytycznego.

![Naruszenie progu krytycznego w poprzednim interwale](../test/media/icon_ltest_3.gif) Wystąpiło naruszenie progu krytycznego w poprzednim interwale.

![Naruszenie progu ostrzeżenia w ostatnim interwale](../test/media/icon_ltest_4.gif) Wystąpiło naruszenie progu ostrzeżenia w ostatnim interwale.

![Naruszenie progu ostrzeżenia w poprzednim interwale](../test/media/icon_ltest_5.gif) Wystąpiło naruszenie progu ostrzeżenia w poprzednim interwale.

Opcjonalnie naruszenia progów mogą być wyświetlane na wykresie. Ikona progu pojawia się na wykresie obok punktu danych, w którym wystąpiło naruszenie progu.

W drzewie liczników ikona naruszenia progu jest propagowana z określonego węzła licznika do węzła głównego. Powoduje to naruszenie dla licznika, który może nie być widoczny w drzewie, ponieważ drzewo nie zostało rozwinięte.

## <a name="view-threshold-violations-on-the-graph"></a>Wyświetl naruszenia progu na wykresie

Na wykresie można wyświetlać naruszenia progów. Podobnie jak w panelu **Counters** , ikony komunikują się z progami naruszeń na grafie. Ikony pojawiają się na wykresie obok punktu danych, w którym wystąpiło naruszenie progu. Jeśli wystąpiło naruszenie progu na liczniku, który nie pojawia się na wykresie, można dodać go do grafu, przeciągając go z panelu **liczniki** do grafu.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz też

- [Określanie zestawów liczników i reguł progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
