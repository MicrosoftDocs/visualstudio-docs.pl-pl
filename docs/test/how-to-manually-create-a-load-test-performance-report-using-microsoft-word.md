---
title: Utwórz raport wydajności testu obciążenia przy użyciu programu Microsoft Word
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f630c0e5c054185dcc0dcb87f553dff8dd2ad8f7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287600"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Instrukcje: ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word

Raporty testów obciążenia programu Microsoft Word można tworzyć ręcznie przez kopiowanie i wklejanie danych z widoku podsumowania Wyniki testów ładowania i wykresu. Do danych, które są prezentowane w widoku podsumowania i widoku wykresy jest stosowany format HTML, podczas ich kopiowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Możesz skopiować zwykły tekst z widoku tabele i zrzuty ekranu z widoku Szczegóły do programu Microsoft Word, ale nie jest on stosowany w formacie HTML i będzie wymagał dodatkowego formatowania i edycji.

> [!TIP]
> Możliwe jest również automatyczne generowanie zorganizowanych raportów programu Microsoft Excel. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopiuj dane widoku podsumowania

1. W **wyniki testów obciążenia**, jeśli widok podsumowania nie jest aktualnie wyświetlany, kliknij przycisk **Podsumowanie** na pasku narzędzi.

2. W widoku Podsumowanie kliknij prawym przyciskiem myszy i wybierz pozycję **Zaznacz wszystko**.

3. W widoku Podsumowanie kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj**. Renderuje to do schowka dane widoku podsumowania w formacie HTML.

4. W programie Microsoft Word wklej dane widoku podsumowania w odpowiedniej lokalizacji.

5. Można teraz modyfikować, formatować i usuwać aspekty kopiowanej zawartości zgodnie z własnymi potrzebami raportowania.

## <a name="copy-graph-view-data"></a>Kopiuj dane widoku wykresu

1. W **wyniki testów obciążenia**, jeśli widok wykresy nie jest aktualnie wyświetlany, wybierz **wykresy** na pasku narzędzi.

2. Obowiązkowe Powiększ konkretny wykres, który chcesz skopiować do dokumentu programu Microsoft Word, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji, zobacz [jak: powiększanie w regionie grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Kontrolka powiększenia widoku wykresu](../test/media/ltest_zoomcontrol.png)

3. Na wykresie, który chcesz skopiować do dokumentu programu Microsoft Word, kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj**.

4. W programie Microsoft Word wklej wykres i powiązane z nim dane tabeli w odpowiedniej lokalizacji.

    > [!WARNING]
    > Nie można skopiować wykresu z pulpitu zdalnego i wkleić go do innej maszyny, ponieważ zostaną skopiowane jedynie informacje tabeli, która jest skojarzona z wykresem, a nie obraz wykresu. Obraz wykresu jest przechowywany w katalogu tymczasowym na maszynie, z której został skopiowany, a druga maszyna nie może wyłuskać tego katalogu.

## <a name="see-also"></a>Zobacz też

- [Zgłoś wyniki testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md)
- [Instrukcje: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
