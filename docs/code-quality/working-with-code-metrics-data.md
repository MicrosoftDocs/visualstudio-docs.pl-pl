---
title: Okno metryk kodu
ms.date: 12/12/2017
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
ms.openlocfilehash: 126360a5cbc39653405d83362ae150edba401fb8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448691"
---
# <a name="use-the-code-metrics-results-window"></a>Korzystanie z okna wyników metryk kodu

W oknie **wyniki metryk kodu** są wyświetlane dane, które są generowane przez analizę metryk kodu. Aby uzyskać więcej informacji na temat wartości danych metryk kodu, zobacz [wartości metryk kodu](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Wyświetl wyniki metryk kodu

Okno **wyników metryki kodu** jest wyświetlane automatycznie podczas generowania wyników metryki kodu. Okno można także wyświetlić w dowolnym momencie.

Można wyświetlić okno wyników metryk kodu przy użyciu jednej z następujących sekwencji menu:

- W menu **Analizuj** wybierz pozycję**wyniki metryk kodu**dla **systemu Windows** > .

- W menu **Widok** wybierz inne**wyniki metryk kodu**dla **systemu Windows** > .

Zostanie otwarte okno **wyników metryki kodu** , nawet jeśli nie zawiera żadnych wyników.

### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu

Jeśli wyniki metryk kodu zostały wygenerowane, rozwiń drzewo w kolumnie **Hierarchia** .

## <a name="filter-code-metrics-results"></a>Filtruj wyniki metryk kodu

Wyniki, które są wyświetlane w oknie **wyników metryk kodu** , można filtrować przy użyciu paska narzędzi u góry. Na przykład możesz chcieć zobaczyć tylko wyniki mające indeks utrzymania poniżej 65.

Pole listy rozwijanej **Filtr** zawiera nazwy kolumn wyników. Gdy filtr jest zdefiniowany, jest dodawany do dolnej części listy wraz z wcięciem. Lista może zawierać 10 ostatnich filtrów, które zostały zdefiniowane.

### <a name="to-filter-the-code-metrics-results"></a>Aby filtrować wyniki metryk kodu

1. Z listy **Filtr** wybierz nazwę kolumny.

2. W polu **min**wpisz wartość minimalną, która ma zostać wyświetlona.

3. W polu **maks**wpisz wartość maksymalną, która ma zostać wyświetlona.

4. Kliknij przycisk **Zastosuj filtr** .

5. Aby wyświetlić szczegóły wyniku, rozwiń drzewo hierarchii.

## <a name="add-remove-and-rearrange-data-columns"></a>Dodawanie, usuwanie i zmiana rozmieszczenia kolumn danych

Kolumny wyników można dodawać lub usuwać z okna **wyników metryk kodu** . Ponadto można zmienić rozmieszczenie kolumn wyników, aby były wyświetlane w pożądanej kolejności.

### <a name="add-or-remove-a-column"></a>Dodawanie lub usuwanie kolumny

1. Kliknij przycisk **Dodaj/Usuń kolumny** lub kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij polecenie **Dodaj/Usuń kolumny**.

1. W oknie dialogowym **Dodawanie/usuwanie kolumn** zaznacz lub usuń zaznaczenie pola wyboru dla kolumny, którą chcesz dodać lub usunąć, a następnie wybierz przycisk **OK**.

### <a name="rearrange-columns"></a>Zmień rozmieszczenie kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** .

1. W oknie dialogowym **Dodawanie/usuwanie kolumn** wybierz kolumnę, którą chcesz przenieść, a następnie wybierz strzałkę w górę lub strzałkę w dół.

1. Gdy kolumna zostanie umieszczona w wybranym miejscu, wybierz **przycisk OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Kopiowanie danych do Schowka lub programu Excel

Można wybrać i skopiować wybrany wiersz danych metryki kodu do Schowka jako ciąg tekstowy, który zawiera jeden wiersz dla nazwy i wartości każdej kolumny danych. Możesz również kliknąć pozycję **Otwórz zaznaczenie w programie Microsoft Excel** , aby wyeksportować wszystkie wyniki metryk kodu do arkusza kalkulacyjnego programu Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Utwórz element roboczy na podstawie wyników metryki kodu

Można utworzyć [Azure Boards](/azure/devops/boards/index?view=vsts) element roboczy, który jest oparty na wynikach w oknie **wyników metryki kodu** . Gdy element roboczy zostanie utworzony, program Visual Studio automatycznie wprowadza tytuł w polu **tytuł** i dane metryk kodu na karcie **historia** .

Aby uzyskać więcej informacji na temat Azure Boards elementów roboczych, zobacz [elementy robocze](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku

1. Kliknij prawym przyciskiem myszy wynik.

2. Wskaż polecenie **Utwórz element roboczy**, a następnie kliknij typ elementu pracy, który chcesz utworzyć (**usterka**, **zadanie**itd.).

3. Wypełnij formularz elementu pracy, wypełniając wszystkie wymagane pola.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać element roboczy.

### <a name="to-create-a-bug-based-on-a-result"></a>Aby utworzyć usterkę na podstawie wyniku

1. Kliknij wynik, aby go zaznaczyć.

2. Kliknij przycisk **Utwórz element roboczy** .

3. Wypełnij formularz elementu pracy, wypełniając wszystkie wymagane pola.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać element roboczy.

## <a name="see-also"></a>Zobacz także

- [Wartości metryk kodu](../code-quality/code-metrics-values.md)
- [Instrukcje: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
