---
title: Tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3deee8d35f06e50dbe22001e8a2fa81b41563e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113444"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Jak: Ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word

Raporty testów ładowania programu Microsoft Word można tworzyć ręcznie, kopiując i wklejając dane z widoku podsumowania Wyniki testu obciążenia i wykresów. Do danych, które są prezentowane w widoku podsumowania i widoku wykresy jest stosowany format HTML, podczas ich kopiowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Można skopiować zwykły tekst z widoku tabel i zrzuty ekranu z widoku szczegółów do programu Microsoft Word, ale nie jest stosowany w formacie HTML i będzie wymagał dodatkowego formatowania i edycji.

> [!TIP]
> Można również automatycznie generować zorganizowane raporty programu Microsoft Excel. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopiowanie danych widoku podsumowania

1. Jeśli **Load Test Results**widok podsumowania nie jest aktualnie wyświetlany, kliknij pozycję **Podsumowanie** na pasku narzędzi, jeśli widok testu obciążenia nie jest wyświetlany.

2. W widoku podsumowania kliknij prawym przyciskiem myszy i wybierz polecenie **Zaznacz wszystko**.

3. W widoku podsumowania kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj**. Renderuje to do schowka dane widoku podsumowania w formacie HTML.

4. W programie Microsoft Word wklej dane widoku podsumowania w żądanej lokalizacji.

5. Można teraz modyfikować, formatować i usuwać aspekty kopiowanej zawartości zgodnie z własnymi potrzebami raportowania.

## <a name="copy-graph-view-data"></a>Kopiowanie danych widoku wykresu

1. Jeśli **Load Test Results**widok wykresy nie jest aktualnie wyświetlany, wybierz **opcję Wykresy** na pasku narzędzi.

2. (Opcjonalnie) Powiększ określony wykres, który chcesz skopiować do dokumentu programu Microsoft Word, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji, zobacz [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Sterowanie powiększeniem widoku wykresu](../test/media/ltest_zoomcontrol.png)

3. Na wykresie, który chcesz skopiować do dokumentu programu Microsoft Word, kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj**.

4. W programie Microsoft Word wklej wykres i skojarzone dane tabeli w żądanej lokalizacji.

    > [!WARNING]
    > Nie można skopiować wykresu z pulpitu zdalnego i wkleić go do innej maszyny, ponieważ zostaną skopiowane jedynie informacje tabeli, która jest skojarzona z wykresem, a nie obraz wykresu. Obraz wykresu jest przechowywany w katalogu tymczasowym na maszynie, z której został skopiowany, a druga maszyna nie może wyłuskać tego katalogu.

## <a name="see-also"></a>Zobacz też

- [Zgłoś wyniki testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md)
- [Jak: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
