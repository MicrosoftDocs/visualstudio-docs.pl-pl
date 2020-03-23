---
title: Korzystanie z legendy wykresu podczas przeprowadzania analizy testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1455c67c3cb6d8dc99aeab91a7bfa63cce009c51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590803"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Legenda widoku Wykresy służy do analizowania testów obciążenia

Widok wykresów analizatora testu obciążenia, zawierają panel legendy, który wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z aktualnie zaznaczonym wykresem.

![Legenda widoku wykresów](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Następujące informacje są zawarte wewnątrz legendy:

- **Pokaż na wykresie:** Użyj pól wyboru, aby określić, czy wiersz dla określonego licznika, takiego jak **Obciążenie użytkownika** lub **Błędy/S,** jest kreślony na wykresie. Zaznacz pole wyboru, jeśli linia ma być wykreślona na wykresie. Wyczyść pole wyboru, aby usunąć linię wydruku z wykresu. Jeśli linia podziału zostanie usunięta, statystyki licznika będą nadal wyświetlane w legendzie.

- **Zakres:** W tej kolumnie jest wyświetlany zakres osi y licznika wydajności. Domyślnie ta wartość będzie automatycznie dostosowywana w miarę zmian zakresu przykładowych danych. Automatycznie skorygowany zakres, zawsze będzie następną potęgą liczby 10, większą niż maksymalna wartość. Obejmuje to negatywne potęgi dziesięciu. Wykres może zawierać wiele liczników, każdy z innym zakresem. Z tego powodu, oś y nie jest oznaczona żadnym określonym zakresem, ale zamiast tego, jest oznaczona wartościami z zakresu 0-100, które reprezentują procent całkowitego zakresu, dla każdego licznika. Na przykład dla licznika o zakresie 1000 punkt danych 60 na osi y będzie odpowiadać wartości 600 dla tego licznika.

    > [!NOTE]
    > Automatyczną regulację wartości zakresu można wyłączyć, blokując zakres do określonej wartości. Gdy zakres jest zablokowany, wszystkie wartości przekraczające zakres, są wyświetlane jako maksymalna wartość, określona w górnej części wykresu. Okno dialogowe **Opcje kreślenia** służy do blokowania zakresu przy określonej wartości.

- **Licznik:** Cztery kolumny o nazwie **Licznik,** **Wystąpienie,** **Kategoria**i **Komputer** razem jednoznacznie identyfikują licznik wydajności.

- **Kolor:** Kolumna **Kolor** pokazuje kolor i styl linii wykreślonych dla licznika wydajności. Okno dialogowe **Opcje kreślenia** umożliwia zmianę koloru lub stylu linii licznika wydajności na wykresie. Okno dialogowe **Opcje wydruku** jest dostępne w menu skrótów legendy.

- **Statystyki:** Kolumny **Min,** **Max**, **Avg** i **Last** pokazują odpowiednie statystyki licznika wydajności. Wartości te odpowiadają danym wyświetlanym na widocznym regionie wykresu. Na przykład jeśli powiększysz region przebiegu, statystyki legendy będą odzwierciedlać wartości, tylko dla powiększonego obszaru. Kolumna "Ostatnia" jest wartością licznika wydajności w ostatnio zakończonym interwale próbkowania.

    > [!NOTE]
    > Ostatnia kolumna wyświetla się tylko w legendzie analizatora testu obciążeniowego podczas uruchomienia testu obciążeniowego.

     Aby uzyskać więcej informacji, zobacz [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Zaznaczenie elementu w legendzie, wykonuje następujące czynności:

- Umożliwia usunięcie elementu zarówno z legendy, jak i wykresu. Kliknij prawym przyciskiem myszy element i wybierz polecenie **Usuń**lub naciśnij klawisz **Delete.**

- Podświetla wykreślony wiersz na wykresie.

- Powoduje, że siatka danych wyświetla dane dla wybranego elementu.

- Umożliwia dostęp do okna dialogowego **Opcje wydruku** licznika.

> [!TIP]
> Przycisk **listy rozwijanej Opcje wykresu** można użyć na pasku narzędzi **Analizator testu obciążenia** i wybrać opcję Pokaż **legendę,** aby wyświetlić lub ukryć panel **Legenda** skojarzony z widokiem wykresu.

## <a name="see-also"></a>Zobacz też

- [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizowanie wyników testu obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
