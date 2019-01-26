---
title: Okno metryk kodów
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea95a5c64a4f3bbe6332542aee84d0ec0b12ec3e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036202"
---
# <a name="use-the-code-metrics-results-window"></a>Korzystanie z okna wyników metryk kodów

**Wyników metryk kodów** okna wyświetla dane, który jest generowany podczas analizy metryki kodu. Aby uzyskać więcej informacji na temat wartości danych metryk kodu zobacz [kodu wartości metryk](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Wyświetlanie wyników metryk kodów

**Wyników metryk kodów** okno jest wyświetlane automatycznie, gdy Generowanie wyników metryk kodów. Możesz również wyświetlić okna, w dowolnym momencie.

Można wyświetlić okno wyników metryk kodów, przy użyciu jednej z następujących sekwencje menu:

- Na **analizy** menu, wybierz **Windows** > **wyników metryk kodów**.

- Na **widoku** menu, wybierz **Windows inne** > **wyników metryk kodów**.

**Wyników metryk kodów** zostanie otwarte okno, nawet wtedy, gdy zawiera on żadnych wyników.

### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu

Jeśli zostały wygenerowane wyników metryk kodów, rozwiń drzewo w **hierarchii** kolumny.

## <a name="filter-code-metrics-results"></a>Filtrowanie wyników metryk kodów

Można filtrować wyniki, które są wyświetlane w **wyników metryk kodów** okna za pomocą paska narzędzi u góry. Na przykład możesz chcieć wyświetlić tylko wyniki, które mają indeks łatwości utrzymania poniżej 65.

**Filtru** pole listy rozwijanej zawiera nazwy kolumn, wyniki. Po zdefiniowaniu filtru jest dodawany do dolnej części listy wraz z wcięciem. Lista może zawierać 10 ostatnich filtrów, które zostały zdefiniowane.

### <a name="to-filter-the-code-metrics-results"></a>Do filtrowania wyników metryk kodów

1.  Z **filtru** , wybierz nazwę kolumny na liście.

2.  W **Min**, wpisz wartość minimalna, który będzie wyświetlany.

3.  W **Max**, wpisz wartość maksymalna ma być wyświetlany.

4.  Kliknij przycisk **Zastosuj filtr** przycisku.

5.  Aby wyświetlić szczegóły wyniku, rozwiń drzewo hierarchii.

## <a name="add-remove-and-rearrange-data-columns"></a>Dodawanie, usuwanie i zmiana rozmieszczenia kolumn danych

Można dodać lub usunąć wyniki kolumny z **wyników metryk kodów** okna. Ponadto, aby były wyświetlane w kolejności, w którym chcesz można zmienić kolejność kolumn wyników.

### <a name="add-or-remove-a-column"></a>Dodawanie lub usuwanie kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku, lub kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** okno dialogowe, zaznacz lub wyczyść pole wyboru w kolumnie, który chcesz dodać lub usunąć, a następnie wybierz **OK**.

### <a name="rearrange-columns"></a>Zmiana rozmieszczenia kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

1. W **Dodaj/Usuń kolumny** okna dialogowego Wybierz kolumnę, którą chcesz przenieść, a następnie wybierz strzałkę w górę lub strzałkę w dół.

1. Jeśli kolumna zostanie umieszczona w miejscu, wybierz **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Kopiowanie danych do Schowka lub programu Excel

Można wybrać i skopiować wybrany wiersz danych metryki kodu do Schowka jako ciąg tekstowy, który zawiera jeden wiersz dla nazwy i wartości wszystkich kolumn danych. Możesz również kliknąć **Otwórz zaznaczenie w programie Microsoft Excel** Aby wyeksportować wszystkie wyniki metryki kodu do arkusza kalkulacyjnego programu Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Utwórz element roboczy, w oparciu o wyniki metryk kodu

Możesz utworzyć [tablice Azure](/azure/devops/boards/index?view=vsts) skutkuje elementu roboczego, który jest oparty na **wyniki metryki kodu** okna. Po utworzeniu elementu roboczego programu Visual Studio automatycznie wprowadzi tytuł w **tytuł** dane metryk pola i kodu pod **historii** kartę.

Aby uzyskać więcej informacji na temat tablic Azure elementów roboczych, zobacz [elementów roboczych](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku

1.  Kliknij prawym przyciskiem myszy wynik.

2.  Wskaż **Utwórz element pracy**, a następnie kliknij typ elementu roboczego, w której chcesz utworzyć (**usterki**, **zadań**, i tak dalej).

3.  Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

### <a name="to-create-a-bug-based-on-a-result"></a>Aby utworzyć usterkę, na podstawie wyniku

1.  Kliknij wynik, aby go zaznaczyć.

2.  Kliknij przycisk **Utwórz element roboczy** przycisku.

3.  Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

## <a name="see-also"></a>Zobacz także

- [Wartości metryk kodów](../code-quality/code-metrics-values.md)
- [Instrukcje: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)