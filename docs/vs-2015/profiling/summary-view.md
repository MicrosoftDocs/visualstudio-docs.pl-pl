---
title: Widok podsumowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: f4346b0e7459ee3c78669ab9178555370ffac16d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545512"
---
# <a name="summary-view"></a>Widok podsumowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania zawiera informacje o najbardziej wydajnych funkcjach lub obiektach w przebiegu profilowania. Ten widok zawiera wykres osi czasu oraz dwie lub więcej list najbardziej kosztownych funkcji lub obiektów opartych na metrykach wydajności metody profilowania. Dane w tym widoku są zależne od metody profilowania, która została użyta (próbkowanie, Instrumentacja lub współbieżność) i czy został zebrany przydział pamięci platformy .NET.  
  
 W przypadku wszystkich widoków podsumowania z wyjątkiem widoku podsumowania danych współbieżności wykres osi czasu w widoku Podsumowanie przedstawia wykorzystanie procesora (CPU) profilowanej aplikacji w czasie, w którym nastąpiło profilowanie.  
  
- Jeśli określisz segment czasu na wykresie, możesz ponownie przeanalizować dane dla tego segmentu lub powiększyć oś czasu do określonego segmentu. Aby uzyskać więcej informacji, zobacz [jak: filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
- Możesz kliknąć funkcję na liście Widok podsumowania, aby otworzyć widok Szczegóły funkcji dla funkcji. Możesz również kliknąć prawym przyciskiem myszy funkcję dla innych opcji widoku.  
  
- Aby zmodyfikować liczbę elementów wyświetlanych na listach widoku podsumowania, otwórz menu **Narzędzia** , wskaż polecenie **Opcje**, a następnie kliknij polecenie **Narzędzia wydajności**. W obszarze **Ustawienia ogólne**zmodyfikuj **liczbę funkcji w widoku podsumowania** .  
  
## <a name="notifications-links"></a>Linki powiadomień  
 Możesz kliknąć linki na liście powiadomień, aby ustawić opcje wyświetlania raportu. Lista znajduje się po prawej stronie wykresu osi czasu.  
  
|Opcja|Opis|  
|-|-|  
|**Pokaż kod niebędący użytkownikiem**<br /><br /> **Pokaż Tylko mój kod**|Niedostępne dla kodu natywnego lub do profilowania danych, które zostały zebrane przy użyciu metody instrumentacji. Przełącza między wyświetlaniem tylko danych z kodu użytkownika (**Pokazywanie tylko mój kod**) i wyświetlaniem danych ze wszystkich kodów, w tym kodu systemowego (**Pokazywanie kodu**niezwiązanego z użytkownikiem). Domyślnie dane są ograniczone do kodu użytkownika. Aby zmienić to ustawienie, zobacz [How to: Filter narzędzia profilowania widoki raportów, aby wyświetlić tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Wyświetl wskazówki**|Wyświetla ostrzeżenia reguły wydajności w oknie **Lista błędów** . Aby uzyskać więcej informacji, zobacz [Używanie reguł wydajności do analizowania danych](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Raport  
 Możesz kliknąć linki na liście raportów, aby otworzyć różne widoki i porównać, zapisać lub filtrować raport. Lista znajduje się po prawej stronie wykresu osi czasu.  
  
|Nazwa|Opis|  
|-|-|  
|**Pokaż przycięte drzewo wywołań**|Wyświetla najbardziej kosztowne ścieżki wykonywania w widoku drzewa wywołań. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md).|  
|**Pokaż linie aktywne**|Niedostępne w przypadku profilowania danych zebranych za pomocą metody instrumentacji. Wyświetla najbardziej kosztowne wiersze kodu źródłowego w widoku wierszy. Aby uzyskać więcej informacji, zobacz [Widok linii](../profiling/lines-view.md).|  
|**Porównaj raporty**|Wyświetla okno dialogowe **Wybieranie plików analizy do porównania** , w którym można określić inny plik danych profilowania do porównania z bieżącym plikiem. Aby uzyskać więcej informacji, zobacz [Porównanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md).|  
|**Eksportuj dane raportu**|Wyświetla okno dialogowe **Eksportuj raport** , w którym można określić co najmniej jeden widok raportu, który ma zostać zapisany jako plik z wartościami rozdzielanymi przecinkami (CSV) lub XML. Aby uzyskać więcej informacji, zobacz [How to: Export narzędzia profilowania Reports](https://msdn.microsoft.com/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Zapisz przeanalizowany raport**|Zapisuje bieżący plik danych profilowania jako plik. vsps, który jest otwierany szybciej w interfejsie dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: saveed Profiling Data Files](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrowanie danych raportu**|Wyświetla okienko filtr raportu profilowania, w którym można określić kryteria ograniczające dane w widoku raportu. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md)|  
|**Przełącz pełny ekran**|Przełącza tryb pełnoekranowy dla widoku raportu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)   
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)
