---
title: Tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a82479fabda0cd64e977af01f87492563a02853f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950075"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Instrukcje: Ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word

Można ręcznie utworzyć raporty testu obciążenia w programie Microsoft Word przez kopiowanie i wklejanie danych z widoku podsumowania wyników testu obciążeniowego i widok wykresów. Do danych, które są prezentowane w widoku podsumowania i widoku wykresy jest stosowany format HTML, podczas ich kopiowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Można kopiować zwykły tekst z widoku tabel i zrzutów ekranu z widoku szczegółów do programu Microsoft Word, ale nie ma zastosowania w formacie HTML i będzie wymagać dodatkowego formatowania i edycji.

> [!TIP]
> Można również wygenerować zorganizowane raporty programu Excel automatycznie. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel za pomocą](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Skopiuj dane widoku podsumowania

1. W **wyniki testu obciążeniowego**, jeśli widok podsumowania nie jest aktualnie wyświetlany, kliknij przycisk **podsumowania** na pasku narzędzi.

2. W widoku podsumowania, kliknij prawym przyciskiem myszy i wybierz **Zaznacz wszystko**.

3. W widoku podsumowania, kliknij prawym przyciskiem myszy i wybierz **kopiowania**. Renderuje to do schowka dane widoku podsumowania w formacie HTML.

4. W programie Microsoft Word wklej dane widoku podsumowania w pożądanej lokalizacji.

5. Można teraz modyfikować, formatować i usuwać aspekty kopiowanej zawartości zgodnie z własnymi potrzebami raportowania.

## <a name="copy-graph-view-data"></a>Kopiowanie danych widoku wykresu

1. W **wyniki testu obciążeniowego**, jeśli wykresy widok nie jest aktualnie wyświetlany, wybierz **wykresów** na pasku narzędzi.

2. (Opcjonalnie) Powiększ określony wykres, który chcesz skopiować do dokumentu programu Microsoft Word, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji, zobacz [jak: Powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Kontrolka powiększenia widoku wykresu](../test/media/ltest_zoomcontrol.png)

3. Na wykresie, który chcesz skopiować do dokumentu programu Microsoft Word, kliknij prawym przyciskiem myszy i wybierz **kopiowania**.

4. W programie Microsoft Word Wklej wykres i skojarzonej tabeli danych w dowolnym miejscu.

    > [!WARNING]
    > Nie można skopiować wykresu z pulpitu zdalnego i wkleić go do innej maszyny, ponieważ zostaną skopiowane jedynie informacje tabeli, która jest skojarzona z wykresem, a nie obraz wykresu. Obraz wykresu jest przechowywany w katalogu tymczasowym na maszynie, z której został skopiowany, a druga maszyna nie może wyłuskać tego katalogu.

## <a name="see-also"></a>Zobacz także

- [Testy obciążenia raport wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md)
- [Instrukcje: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)