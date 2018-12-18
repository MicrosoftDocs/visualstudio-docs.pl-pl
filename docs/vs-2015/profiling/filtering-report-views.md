---
title: Filtrowanie widoków raportów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5ce703fdc3b0d20feda83b59706e7c4792d2ade
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753435"
---
# <a name="filtering-report-views"></a>Filtrowanie widoków raportów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Filtry można zastosować do pliku danych, aby ograniczyć dane profilowania, który jest wyświetlany w widokach raport dotyczący wydajności i wyeksportowane pliki raportu profilowania. Można ograniczyć raport, aby dane między wartości sygnatur czasowych i umożliwia ograniczenie danych do określonych procesów i wątków. Można zapisać w pliku filtrów i utworzenie filtru na inny plik danych profilowania, importując zapisany filtr.  
  
 Można również ograniczyć raportu do segmentu czasu za pomocą graficznego osi czasu w widoku Podsumowanie. Zobacz [porady: filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Aby wykluczyć systemu i kod innych firm z raportu, zobacz [jak: Filtr profilowania narzędzia widoków raportu w celu wyświetlania tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-profiler-report-filter"></a>Aby utworzyć filtr raportów profilera  
  
1.  Jeśli nie zostanie wyświetlone okno Filtr widoku raportów wydajności, kliknij przycisk **Pokaż filtr** na pasku narzędzi w widoku raportu wydajności.  
  
     Filtr widoku raportów wydajności znajduje się tabela. Każdy wiersz w tabeli reprezentuje klauzuli filtru. Możesz dodać dowolną liczbę klauzul do filtru.  
  
2.  Dla każdej klauzuli, który chcesz dodać do filtru wybierz lub wprowadź wartości w następujących polach wiersza.  
  
    |Pole|Opis|  
    |-----------|-----------------|  
    |**I/lub**|Wybierz **i** Jeśli tę klauzulę i dalej klauzula musi mieć wartość true do Dopasuj wynik. Wybierz **lub** , jeśli ta klauzula lub klauzuli dalej może być wartość true, aby dopasować wynik.|  
    |**Pole**|Wybierz pole raportu do użycia w klauzuli filtru z wyświetlonej listy pól danych.|  
    |**Operator**|Wybierz operator, który określa relację, która ma w klauzuli między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większa niż lub równe|  
    |**Wartość**|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|  
  
3.  
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Aby utworzyć filtr raportów profilera w widoku raportu znaczniki  
  
1. Wybierz **znaczniki** z **bieżący widok** listy na pasku narzędzi w widoku raportu wydajności.  
  
    Zostanie wyświetlony raport profiler znaczników.  
  
2. Wybierz ETW lub próbkowania, nawet, którą chcesz użyć jako punktu wyjścia raportu.  
  
3. Naciśnij i przytrzymaj klawisz CTRL i kliknij zdarzenie, które chcesz użyć jako punktu końcowego raportu.  
  
4. Kliknij prawym przyciskiem myszy, a następnie kliknij jedną z następujących opcji:  
  
   - **Dodaj filtr znaczników** tworzy klauzul filtru, korzystających z kolumny Oznacz jako pole filtru.  
  
   - **Dodaj filtr sygnatury czasowe** tworzy klauzul filtru, korzystających z jako pole filtru w kolumnie sygnatura czasowa w milisekundach.  
  
     Dwie opcje filtrowania bieżącego pliku danych, w tym samym początkowego i punktu końcowego. Jedną z opcji może być lepiej, jeśli eksportujesz filtru do użycia w innych raportach.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Aby załadować istniejący filtr z pliku  
  
1.  Kliknij na pasku narzędzi widoku raportu wydajności **filtru importu**.  
  
     **Załaduj filtr** zostanie wyświetlone okno dialogowe.  
  
2.  Określ lokalizację i nazwę pliku filtru (.vspf) można załadować.  
  
#### <a name="to-execute-a-filter"></a>Wykonywanie filtru  
  
-   Kliknij na pasku narzędzi widoku raportu wydajności **wykonaj filtr**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Aby zatrzymać filtr, który trwa zbyt długo, można wykonać  
  
-   Kliknij na pasku narzędzi widoku raportu wydajności **zatrzymać filtru**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Aby usunąć filtr w widoku raportu  
  
1.  Usuń wiersze klauzul filtr widoku raportów wydajności.  
  
2.  Kliknij na pasku narzędzi widoku raportu wydajności **wykonaj filtr**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Aby zapisać filtr do pliku  
  
1.  Kliknij na pasku narzędzi widoku raportu wydajności **Eksportuj filtr**.  
  
     **Zapisywanie filtru** zostanie wyświetlone okno dialogowe.  
  
2.  Określ lokalizację i nazwę pliku filtru (.vspf) można zapisać.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie widoków raportów narzędzi do oceny wydajności](../profiling/customizing-performance-tools-report-views.md)



