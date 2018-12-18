---
title: Widok podsumowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdacfcba18d465685053cdea4581a5806c25db9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757327"
---
# <a name="summary-view"></a>Widok podsumowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania Wyświetla informacje o wydajności najdroższych funkcje lub obiekty podczas uruchomienia profilowania. Ten widok zawiera wykres osi czasu i co najmniej dwóch list najbardziej kosztowne funkcje lub obiekty w oparciu metryki wydajności metody profilowania. Dane w tym widoku jest zależna od metody profilowania, który został użyty (próbkowanie, Instrumentacja lub współbieżności) i tego, czy zebrano alokacji pamięci .NET.  
  
 Wszystkie widoki podsumowanie oprócz widok podsumowania danych współbieżności wykres osi czasu w widoku podsumowania przedstawia użycie procesora (CPU) profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania.  
  
-   Jeśli określisz odcinek czasu na wykresie, możesz przeanalizować dane dla tego segmentu lub zmieniaj segment, który określiłeś osi czasu. Aby uzyskać więcej informacji, zobacz [jak: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   Możesz kliknąć funkcji na liście Widok podsumowania, aby otworzyć widok szczegółów funkcji dla tej funkcji. Możesz również kliknąć prawym przyciskiem myszy funkcję dla innych opcji widoku.  
  
-   Aby zmodyfikować liczbę elementów, które są wyświetlane na listach widok podsumowania, otwórz **narzędzia** menu wskaż **opcje**, a następnie kliknij przycisk **narzędzia do oceny wydajności**. W obszarze **ustawienia ogólne**, zmodyfikuj **liczba funkcji w widoku podsumowania** ustawienie.  
  
## <a name="notifications-links"></a>Linki powiadomienia  
 Możesz kliknąć linki, aby ustawić opcje wyświetlania raportu na liście powiadomień. Lista jest po prawej stronie wykres osi czasu.  
  
|||  
|-|-|  
|**Pokaż kod niezwiązany z użytkownikiem**<br /><br /> **Pokaż tylko mój kod**|Nie są dostępne dla kodu natywnego lub dane, które zostały zebrane przy użyciu metody Instrumentacji profilowania. Przełączenie między wyświetlaniem tylko dane z kodu użytkownika (**Pokaż tylko mój kod**) i wyświetlanie danych z całego kodu, w tym kodu systemowego (**Pokaż kod niezwiązany z użytkownikiem**). Domyślnie dane są ograniczone do kodu użytkownika. Aby zmienić to ustawienie, zobacz [jak: Filtr profilowania narzędzia widoków raportu w celu wyświetlania tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Wyświetl asystę**|Wyświetla ostrzeżenia reguły wydajności w **lista błędów** okna. Aby uzyskać więcej informacji, zobacz [przy użyciu reguł wydajności do analizowania danych](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Raport  
 Możesz kliknąć linki Otwórz różne widoki i do porównania, Zapisz lub filtrować raport na liście raportów. Lista jest po prawej stronie wykres osi czasu.  
  
|||  
|-|-|  
|**Pokaż przycięte drzewo wywołań**|Wyświetla widok drzewa wywołań najbardziej kosztowne wykonania ścieżki. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md).|  
|**Pokaż aktywne wiersze**|Nie jest dostępna dla danych, które zostały zebrane przy użyciu metody Instrumentacji profilowania. Wyświetla najbardziej kosztowne wierszy kodu źródłowego w widoku wierszy. Aby uzyskać więcej informacji, zobacz [widok linii](../profiling/lines-view.md).|  
|**Porównanie raportów**|Wyświetla **wybierz pliki analizy porównanie** okno dialogowe, w którym można określić inny plik danych profilowania do porównania z bieżącym pliku. Aby uzyskać więcej informacji, zobacz [porównywanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md).|  
|**Eksportuj dane raportu**|Wyświetla **Eksportowanie raportu** okno dialogowe, w którym można określić jeden lub więcej widoków raportu można zapisać w formacie wartości rozdzielanych przecinkami (.csv) lub plików XML. Aby uzyskać więcej informacji, zobacz [porady: eksportowanie raportów narzędzi profilowania](http://msdn.microsoft.com/en-us/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Zapisz przeanalizowany raport**|Zapisuje bieżący plik danych profilowania w postaci pliku .vsps, który zostanie otwarty szybciej w interfejsie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie analizowane profilowania pliki danych](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtruj dane raportu**|Wyświetla profilowania okienko filtru raportu, na której można określić kryteria, aby ograniczyć dane w widoku raportu. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md)|  
|**Przełącz widok pełnoekranowy**|Włącza lub wyłącza tryb pełnoekranowy dla widoku raportu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)   
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)



