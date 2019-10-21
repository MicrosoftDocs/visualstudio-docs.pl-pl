---
title: Praca z danymi metryk kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645705"
---
# <a name="working-with-code-metrics-data"></a>Praca z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W oknie **wyniki metryk kodu** są wyświetlane dane, które są generowane przez analizę metryk kodu. Aby uzyskać więcej informacji na temat wartości danych metryk kodu, zobacz [wartości metryk kodu](../code-quality/code-metrics-values.md).

 Ten temat zawiera następujące sekcje:

- [Okno wyników metryk kodu](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Wyświetlanie wyników metryk kodu](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtrowanie wyników metryk kodu](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Dodawanie, usuwanie i zmiana układu kolumn danych](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Kopiowanie danych do Schowka lub programu Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Tworzenie elementu pracy na podstawie wyników metryki kodu](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="BKMK_CodeMetricsResultsWindow"></a>Okno wyników metryk kodu
 Okno **wyników metryk kodu** zawiera pasek narzędzi u góry i kolumny, aby wyświetlić obliczone wyniki.

|Kolumna|Opis|
|------------|-----------------|
|**Hierarchiczn**|Kolumna **Hierarchia** zawiera widok drzewa hierarchii kodu, który można rozwinąć lub zwinąć, aby wyświetlić żądany poziom szczegółowości. W pozostałych kolumnach są wyświetlane obliczone wyniki. Można ukryć lub rozmieścić kolumny wynikowe.|
|**Łatwość utrzymania**|Kolumna **łatwość utrzymania** zawiera ikonę oprócz wyniku liczbowego. Zielona ikona wskazuje stosunkowo wysoki stopień utrzymania. Żółta ikona wskazuje umiarkowany stopień utrzymania. Czerwona ikona wskazuje na małą łatwość utrzymania i potencjalne problemy. Te wskaźniki kolorów odpowiadają kategoriom ważności, które są używane przez regułę FxCop AvoidUnmaintainableCode. Ta zasada wyzwala błąd, jeśli indeks utrzymania jest mniejszy niż 10, ostrzeżenie, jeśli indeks jest z zakresu od 10 do 20, a nie błędu ani Ostrzeżenia, jeśli indeks jest większy niż 20. Indeks utrzymania jest syntezą trzech metryk: cyklomatyczna złożoności, wierszy kodu i złożoności obliczeniowej. Wartości nie są wyrażone w jednostkach.|

## <a name="BKMK_DisplayingCodeMetricsResults"></a>Wyświetlanie wyników metryk kodu
 Okno wyników metryki kodu jest wyświetlane automatycznie podczas generowania wyników metryki kodu. Okno można także wyświetlić w dowolnym momencie.

#### <a name="to-display-the-code-metrics-results-window"></a>Aby wyświetlić okno wyników metryk kodu

- W menu **Analizuj** kliknij pozycję **Windows** , a następnie kliknij pozycję **wyniki metryk kodu**.

     \- lub-

- W menu **Widok** wskaż **inne okna** , a następnie kliknij pozycję **wyniki metryki kodu**.

     Okno wyników metryk kodu jest wyświetlane nawet wtedy, gdy nie zawiera żadnych wyników.

#### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu

- Jeśli wyniki metryk kodu zostały wygenerowane, rozwiń drzewo w kolumnie **Hierarchia** .

## <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrowanie wyników metryk kodu
 Wyniki, które są wyświetlane w oknie **wyników metryk kodu** , można filtrować przy użyciu paska narzędzi u góry. Na przykład możesz chcieć zobaczyć tylko wyniki mające indeks utrzymania poniżej 65.

 Pole listy rozwijanej **Filtr** zawiera nazwy kolumn wyników. Gdy filtr jest zdefiniowany, jest dodawany do dolnej części listy wraz z wcięciem. Lista może zawierać maksymalnie dziesięć ostatnich filtrów, które zostały zdefiniowane.

#### <a name="to-filter-the-code-metrics-results"></a>Aby filtrować wyniki metryk kodu

1. Z listy **Filtr** wybierz nazwę kolumny.

2. W polu **min**wpisz wartość minimalną, która ma zostać wyświetlona.

3. W polu **maks**wpisz wartość maksymalną, która ma zostać wyświetlona.

4. Kliknij przycisk **Zastosuj filtr** .

5. Aby wyświetlić szczegóły wyniku, rozwiń drzewo hierarchii.

## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Dodawanie, usuwanie i zmiana układu kolumn danych
 Kolumny wyników można dodawać lub usuwać z okna **wyników metryk kodu** . Ponadto można zmienić rozmieszczenie kolumn wyników, aby były wyświetlane w pożądanej kolejności.

#### <a name="to-remove-a-column"></a>Aby usunąć kolumnę

1. Kliknij przycisk **Dodaj/Usuń kolumny** .

     \- lub-

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij polecenie **Dodaj/Usuń kolumny**.

2. W oknie dialogowym **Dodaj/Usuń kolumny** Usuń zaznaczenie pola wyboru dla kolumny, która ma zostać usunięta, a następnie kliknij przycisk **OK**.

#### <a name="to-add-a-previously-removed-column"></a>Aby dodać wcześniej usuniętą kolumnę

1. Kliknij przycisk **Dodaj/Usuń kolumny** .

     \- lub-

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij polecenie **Dodaj/Usuń kolumny**.

2. W oknie dialogowym **Dodawanie/usuwanie kolumn** zaznacz pole wyboru dla kolumny, która ma zostać dodana, a następnie kliknij przycisk **OK**.

#### <a name="to-rearrange-columns"></a>Aby zmienić rozmieszczenie kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** .

     \- lub-

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij polecenie **Dodaj/Usuń kolumny**.

2. W oknie dialogowym **Dodawanie/usuwanie kolumn** wybierz kolumnę, którą chcesz przenieść, a następnie kliknij strzałkę w górę lub strzałkę w dół.

3. Gdy kolumna zostanie umieszczona w żądanym miejscu, kliknij przycisk **OK**.

## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Kopiowanie danych do Schowka lub programu Excel
 Można wybrać i skopiować wybrany wiersz danych metryki kodu do Schowka jako ciąg tekstowy, który zawiera jeden wiersz dla nazwy i wartości każdej kolumny danych. Możesz również kliknąć pozycję **Otwórz listę w programie Microsoft Excel** , aby wyeksportować wszystkie wyniki metryk kodu do arkusza kalkulacyjnego programu Excel

## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Tworzenie elementu pracy na podstawie wyników metryki kodu
 Można utworzyć [!INCLUDE[esprfound](../includes/esprfound-md.md)] element roboczy, który jest oparty na wynikach w oknie **wyników metryki kodu** . Po utworzeniu elementu pracy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie wprowadza tytuł w polu **tytuł** i dane metryk kodu na karcie **historia** .

 Aby uzyskać więcej informacji na temat tworzenia elementów roboczych, zobacz temat [Tworzenie &#91;przekierowanego&#93;elementu pracy](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku

1. Kliknij prawym przyciskiem myszy wynik.

2. Wskaż polecenie **Utwórz element roboczy**, a następnie kliknij typ elementu pracy, który chcesz utworzyć (**usterka**, **zadanie**itd.).

3. Wypełnij formularz elementu pracy, wypełniając wszystkie wymagane pola.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać element roboczy.

#### <a name="to-create-a-bug-based-on-a-result"></a>Aby utworzyć usterkę na podstawie wyniku

1. Kliknij wynik, aby go zaznaczyć.

2. Kliknij przycisk **Utwórz element roboczy** .

3. Wypełnij formularz elementu pracy, wypełniając wszystkie wymagane pola.

4. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać element roboczy.

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
