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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590803"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Korzystanie z legendy widoku wykresy do analizowania testów obciążenia

Widok wykresów analizatora testu obciążenia, zawierają panel legendy, który wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z aktualnie zaznaczonym wykresem.

![Legenda widoku wykresów](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Następujące informacje są zawarte wewnątrz legendy:

- **Pokaż na grafie:** Użyj pól wyboru, aby określić, czy linia dla określonego licznika, taka jak **obciążenie użytkownika** lub **Błędy/s**, jest kreślone na wykresie. Zaznacz pole wyboru, jeśli chcesz, aby linia była kreślone na wykresie. Wyczyść pole wyboru, aby usunąć wiersz kreślenia z grafu. Jeśli linia podziału zostanie usunięta, statystyki licznika będą nadal wyświetlane w legendzie.

- **Zakres:** W tej kolumnie jest wyświetlany zakres osi y licznika wydajności. Domyślnie ta wartość zostanie automatycznie dostosowana jako zakres przykładowych danych zmian. Automatycznie skorygowany zakres, zawsze będzie następną potęgą liczby 10, większą niż maksymalna wartość. Obejmuje to negatywne potęgi dziesięciu. Wykres może zawierać wiele liczników, każdy z innym zakresem. Z tego powodu, oś y nie jest oznaczona żadnym określonym zakresem, ale zamiast tego, jest oznaczona wartościami z zakresu 0-100, które reprezentują procent całkowitego zakresu, dla każdego licznika. Na przykład dla licznika o zakresie 1000 punkt danych 60 na osi y będzie odpowiadać wartości 600 dla tego licznika.

    > [!NOTE]
    > Można wyłączyć automatyczne dopasowywanie wartości zakresu, blokując zakres do określonej wartości. Gdy zakres jest zablokowany, wszystkie wartości przekraczające zakres, są wyświetlane jako maksymalna wartość, określona w górnej części wykresu. Użyj okna dialogowego **Opcje wykresu** , aby zablokować zakres pod określoną wartością.

- **Licznik:** Cztery kolumny o nazwie **Counter**, **instance**, **Category**i **Computer** jednoznacznie identyfikują licznik wydajności.

- **Kolor:** Kolumna **Color** pokazuje kolor i styl linii wykreślonego wiersza dla licznika wydajności. Za pomocą okna dialogowego **Opcje wykresu** Zmień kolor lub styl linii licznika wydajności wykresu. Okno dialogowe **Opcje wykresu** jest dostępne z menu skrótów legendy.

- **Statystyki:** Kolumny **min**, **Max**, **AVG** i **Last** przedstawiają odpowiednie statystyki dla licznika wydajności. Te wartości odpowiadają danym wyświetlanym w widocznym regionie grafu. Na przykład jeśli powiększysz region przebiegu, statystyki legendy będą odzwierciedlać wartości, tylko dla powiększonego obszaru. Kolumna "Last" jest wartością licznika wydajności dla ostatnio wykonanego interwału próbkowania.

    > [!NOTE]
    > Ostatnia kolumna wyświetla się tylko w legendzie analizatora testu obciążeniowego podczas uruchomienia testu obciążeniowego.

     Aby uzyskać więcej informacji, zobacz [jak: powiększanie w regionie grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Zaznaczenie elementu w legendzie, wykonuje następujące czynności:

- Umożliwia usunięcie elementu z legendy i grafu. Kliknij prawym przyciskiem myszy element i wybierz polecenie **Usuń**lub naciśnij klawisz **delete** .

- Podświetla kreślony wiersz na wykresie.

- Powoduje, że siatka danych wyświetla dane dla wybranego elementu.

- Pozwala uzyskać dostęp do okna dialogowego **Opcje wykresu** dla licznika.

> [!TIP]
> Możesz użyć przycisku **listy rozwijanej opcje wykresu** na pasku narzędzi **analizatora testu obciążenia** i wybrać **Pokaż legendę** , aby pokazać lub ukryć panel **legendy** , który jest skojarzony z widokiem wykresu.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: powiększanie w regionie wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
