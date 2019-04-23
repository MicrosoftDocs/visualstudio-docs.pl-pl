---
title: Praca z danymi metryk kodu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4d206785991d37147d9d55d89947776a94b2ac4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111301"
---
# <a name="working-with-code-metrics-data"></a>Praca z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Wyników metryk kodów** okna wyświetla dane, który jest generowany podczas analizy metryki kodu. Aby uzyskać więcej informacji na temat wartości danych metryk kodu zobacz [wartości metryk kodów](../code-quality/code-metrics-values.md).  
  
 Ten temat zawiera następujące sekcje:  
  
- [Okno wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
- [Wyświetlanie wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
- [Filtrowanie wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
- [Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
- [Kopiowanie danych do Schowka lub programu Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
- [Tworzenie elementu roboczego, w oparciu o wyniki metryk kodu](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
## <a name="BKMK_CodeMetricsResultsWindow"></a> Okno wyników metryk kodów  
 **Wyników metryk kodów** okno ma pasku narzędzi u góry i kolumn w celu wyświetlenia wyników obliczeń.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Hierarchia**|**Hierarchii** kolumna zawiera hierarchię kodu, który można rozwinąć lub zwinąć było widać poziom szczegółowości, który ma w widoku drzewa. Pozostałe kolumny pokazują obliczone wyniki. Można ukryć lub zmienić kolejność kolumn wynik, jak chcesz.|  
|**łatwość konserwacji**|**Łatwości utrzymania** kolumna zawiera ikonę, oprócz wyniku numerycznego. Zielona ikona wskazuje stosunkowo wysoki stopień łatwości utrzymania. Żółta ikona wskazuje umiarkowane stopień łatwości utrzymania. Czerwona ikona wskazuje, niski łatwość utrzymania, a punkt potencjalne problemy. Wskaźniki te kolor odpowiadać kategorii ważności, które są używane przez reguły programu FxCop AvoidUnmaintainableCode. Ta reguła jest uruchamiana błąd, jeśli indeks łatwości utrzymania jest mniejszy niż 10, ostrzeżenie, jeśli indeks jest między 10 i 20, a błąd ani ostrzeżenia, jeśli indeks jest większy niż 20. Indeks łatwości utrzymania jest syntezy trzy metryki: złożoność cyklomatyczna, wierszy kodu oraz złożoność obliczeniową. Wartości nie jest wyrażona w jednostkach.|  
  
## <a name="BKMK_DisplayingCodeMetricsResults"></a> Wyświetlanie wyników metryk kodów  
 Zostanie wyświetlone okno wyników metryk kodów automatycznie, gdy Generowanie wyników metryk kodów. Możesz również wyświetlić okna, w dowolnym momencie.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Aby wyświetlić okno wyników metryk kodów  
  
- Na **analizy** menu, kliknij przycisk **Windows** a następnie kliknij przycisk **wyników metryk kodów**.  
  
     \- lub —  
  
- Na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **wyników metryk kodów**.  
  
     Zostanie wyświetlone okno wyników metryk kodów, nawet wtedy, gdy zawiera on żadnych wyników.  
  
#### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu  
  
- Jeśli zostały wygenerowane wyników metryk kodów, rozwiń drzewo w **hierarchii** kolumny.  
  
## <a name="BKMK_FilteringCodeMetricsResults"></a> Filtrowanie wyników metryk kodów  
 Można filtrować wyniki, które są wyświetlane w **wyników metryk kodów** okna za pomocą paska narzędzi u góry. Na przykład możesz chcieć wyświetlić tylko wyniki, które mają indeks łatwości utrzymania poniżej 65.  
  
 **Filtru** pole listy rozwijanej zawiera nazwy kolumn, wyniki. Po zdefiniowaniu filtru jest dodawany do dolnej części listy wraz z wcięciem. Lista może zawierać dziesięć ostatnich filtrów, które zostały zdefiniowane.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Do filtrowania wyników metryk kodów  
  
1. Z **filtru** , wybierz nazwę kolumny na liście.  
  
2. W **Min**, wpisz wartość minimalna, który będzie wyświetlany.  
  
3. W **Max**, wpisz wartość maksymalna ma być wyświetlany.  
  
4. Kliknij przycisk **Zastosuj filtr** przycisku.  
  
5. Aby wyświetlić szczegóły wyniku, rozwiń drzewo hierarchii.  
  
## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych  
 Można dodać lub usunąć wyniki kolumny z **wyników metryk kodów** okna. Ponadto, aby były wyświetlane w kolejności, w którym chcesz można zmienić kolejność kolumn wyników.  
  
#### <a name="to-remove-a-column"></a>Aby usunąć kolumnę  
  
1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \- lub —  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2. W **Dodaj/Usuń kolumny** okno dialogowe, wyczyść pole wyboru dla kolumny, które chcesz usunąć, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Aby dodać kolumnę wcześniej usuniętych  
  
1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \- lub —  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2. W **Dodaj/Usuń kolumny** okna dialogowego pole, zaznacz pole wyboru dla kolumny, które chcesz dodać, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-rearrange-columns"></a>Aby zmienić kolejność kolumn  
  
1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \- lub —  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2. W **Dodaj/Usuń kolumny** okna dialogowego Wybierz kolumnę, którą chcesz przenieść, a następnie kliknij przycisk strzałki w górę lub strzałkę w dół.  
  
3. Jeśli kolumna zostanie umieszczona w miejscu, kliknij przycisk **OK**.  
  
## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Kopiowanie danych do Schowka lub programu Excel  
 Można wybrać i skopiować wybrany wiersz danych metryki kodu do Schowka jako ciąg tekstowy, który zawiera jeden wiersz dla nazwy i wartości wszystkich kolumn danych. Możesz również kliknąć **Otwórz listę w programie Microsoft Excel** Aby wyeksportować wszystkie wyniki metryki kodu do arkusza kalkulacyjnego programu Excel  
  
## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Tworzenie elementu roboczego, w oparciu o wyniki metryk kodu  
 Możesz utworzyć [!INCLUDE[esprfound](../includes/esprfound-md.md)] skutkuje elementu roboczego, który jest oparty na **wyniki metryki kodu** okna. Po utworzeniu elementu roboczego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie wstawia tytuł w **tytuł** dane metryk pola i kodu pod **historii** kartę.  
  
 Aby uzyskać więcej informacji na temat tworzenia elementów roboczych, zobacz [Utwórz element roboczy &#91;przekierowanie&#93;](http://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku  
  
1. Kliknij prawym przyciskiem myszy wynik.  
  
2. Wskaż **Utwórz element pracy**, a następnie kliknij typ elementu roboczego, w której chcesz utworzyć (**usterki**, **zadań**, i tak dalej).  
  
3. Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Aby utworzyć usterkę, na podstawie wyniku  
  
1. Kliknij wynik, aby go zaznaczyć.  
  
2. Kliknij przycisk **Utwórz element roboczy** przycisku.  
  
3. Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.  
  
4. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Instrukcje: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
