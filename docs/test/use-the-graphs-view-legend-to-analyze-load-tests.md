---
title: Korzystanie z legendy wykresu do analizowania testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 082b3da934e602aef2f0c4eefcfffc45da2c40f0
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896084"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Korzystanie z legendy wykresu przeprowadzania analizy testów obciążenia

Widok wykresów analizatora testu obciążenia, zawierają panel legendy, który wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z aktualnie zaznaczonym wykresem.

![Widok wykresów — Legenda](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Następujące informacje są zawarte wewnątrz legendy:

-   **Pokaż na wykresie:** Użyj pól wyboru, aby określić, czy wiersz dla określonego licznika, takich jak **obciążenie użytkownikami** lub **błędy na sekundę**, jest wykreślany na wykresie. Zaznacz pole wyboru, jeśli chcesz, aby wiersz, który ma być oznaczane na wykresach na wykresie. Wyczyść pole wyboru, aby usunąć wiersz z wykresu. Jeśli linia podziału zostanie usunięta, statystyki licznika będą nadal wyświetlane w legendzie.

-   **Zakres:** tej kolumnie jest wyświetlana zakres osi y licznika wydajności. Domyślnie ta wartość będzie automatycznie dopasowywać jako zakres zmiany danych przykładowych. Automatycznie skorygowany zakres, zawsze będzie następną potęgą liczby 10, większą niż maksymalna wartość. Obejmuje to negatywne potęgi dziesięciu. Wykres może zawierać wiele liczników, każdy z innym zakresem. Z tego powodu, oś y nie jest oznaczona żadnym określonym zakresem, ale zamiast tego, jest oznaczona wartościami z zakresu 0-100, które reprezentują procent całkowitego zakresu, dla każdego licznika. Na przykład dla licznika o zakresie 1000 punkt danych 60 na osi y będzie odpowiadać wartości 600 dla tego licznika.

    > [!NOTE]
    > Blokowanie zakresu do określonej wartości, można wyłączyć automatyczne zakresu dopasowania wartości. Gdy zakres jest zablokowany, wszystkie wartości przekraczające zakres, są wyświetlane jako maksymalna wartość, określona w górnej części wykresu. Użyj **Opcje wykresu** okno dialogowe, aby zablokować zakresu w określonej wartości.

-   **Licznik:** cztery kolumny o nazwie **licznika**, **wystąpienia**, **kategorii**, i **komputera** razem jednoznacznie Określ licznik wydajności.

-   **Kolor:** **kolor** kolumna pokazuje styl linii linii wykreślona licznika wydajności. Użyj **Opcje wykresu** okno dialogowe, aby zmienić kolor lub wiersza stylu licznika wydajności na wykresie. **Opcje wykresu** okno dialogowe jest dostępne z menu skrótów legendy.

-   **Statystyki:** **Min**, **Max**, **Avg** i **ostatniego** kolumn pokazują odpowiednie statystyki wydajności Licznik. Te wartości odpowiadają danych, który jest wyświetlany na widocznych obszaru wykresu. Na przykład jeśli powiększysz region przebiegu, statystyki legendy będą odzwierciedlać wartości, tylko dla powiększonego obszaru. Kolumna "Last" jest wartość licznika wydajności z ostatnio wykonanych interwałem próbkowania.

    > [!NOTE]
    > Ostatnia kolumna wyświetla się tylko w legendzie analizatora testu obciążeniowego podczas uruchomienia testu obciążeniowego.

     Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Zaznaczenie elementu w legendzie, wykonuje następujące czynności:

-   Umożliwia elementu do usunięcia z wykresu i legenda. Albo kliknij prawym przyciskiem myszy element i wybierz **Usuń**, lub naciśnij **Usuń** klucza.

-   Wyróżnia wykreślona linii na wykresie.

-   Powoduje, że siatce danych wyświetlić dane dla wybranego elementu.

-   Zapewnia dostęp do **Opcje wykresu** okno dialogowe licznika.

> [!TIP]
> Możesz użyć **menu rozwijane Opcje wykresu** znajdujący się w **analizatora testu obciążenia** narzędzi i wybierz pozycję **Pokaż legendę** pokazać lub ukryć **legendy** Panel, który jest skojarzony z widokiem wykresu.

## <a name="see-also"></a>Zobacz także

- [Porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
