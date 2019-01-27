---
title: 'Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: baa5381013e955dcf4b8e301bba52a28e39bfc18
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779775"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W oknie czujki równoległej może jednocześnie wyświetlać wartości, które zawiera jedno wyrażenie, w wielu wątkach. Każdy wiersz reprezentuje wątek, który jest uruchomiony w aplikacji, ale wątek może być reprezentowany w wielu wierszach. Dokładniej mówiąc każdy wiersz reprezentuje wywołanie funkcji, w których funkcja Podpis pasuje do funkcji w bieżącej ramki stosu. Można sortować, zmienić kolejność, Usuń i grupować elementy, które w kolumnach. Możesz Flaga, Usuń flagę, blokowanie (zawieszenie) i Odblokuj wątki (Wznów). Następujące kolumny są wyświetlane w **równoległego wyrażenia kontrolnego** okna:  
  
- Kolumna flagi, w którym można oznaczyć wątek, który chcesz zwrócić szczególną uwagę.  
  
- Kolumna ramki, w której Strzałka wskazuje wybraną ramkę.  
  
- Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelków, zadania i wątku.  
  
  > [!TIP]
  >  Należy otworzyć **zadanie równoległe** okno, aby wyświetlić informacje o zadaniu w **równoległego wyrażenia kontrolnego** okna.  
  
-  **\<Dodaj wyrażenie kontrolne >** kolumny, w którym należy wprowadzić wyrażenia, aby obejrzeć.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Aby wyświetlić okno czujki równoległej  
  
1.  Ustaw punkt przerwania w kodzie.  
  
2.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja do osiągnięcia punktu przerwania.  
  
3.  Na pasku menu wybierz **debugowania**, **Windows**, **równoległego wyrażenia kontrolnego**, a następnie wybierz Okno czujki. Możesz otworzyć maksymalnie cztery systemu windows.  
  
### <a name="to-add-a-watch-expression"></a>Aby dodać wyrażenia kontrolnego  
  
-   Wybierz  **\<Dodaj wyrażenie kontrolne >** , a następnie określ wyrażenia kontrolnego.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Flaga lub usuń flagę wątku  
  
-   Wybierz kolumny flag wiersza, lub Otwórz menu skrótów dla wątku i wybierz **flagi** lub **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Kliknij przycisk Pokaż tylko oflagowane w lewym górnym rogu **równoległego wyrażenia kontrolnego** okna.  
  
### <a name="to-switch-frames"></a>Aby przełączyć ramki  
  
-   Kliknij dwukrotnie kolumnę ramki. (Klawiatura: Zaznacz wiersz i naciśnij klawisz Enter).  
  
### <a name="to-sort-a-column"></a>Aby posortować kolumnę  
  
-   Wybierz nagłówek kolumny.  
  
### <a name="to-group-threads"></a>Grupa wątków  
  
-   Otwórz menu skrótów dla okno czujki równoległej, wybierz polecenie **Group By**, a następnie wybierz element odpowiednie podmenu.  
  
### <a name="to-freeze-or-thaw-threads"></a>Na blokowanie lub odblokowywanie wątków  
  
-   Otwórz menu skrótów dla wiersza, a następnie wybierz **Freeze** lub **Odblokuj**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Aby wyeksportować dane w oknie czujki równoległej  
  
-   Wybierz **Otwórz w programie Excel** przycisk, a następnie wybierz **Otwórz w programie Excel** lub **Eksportuj do pliku CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Aby filtrować według wyrażenie warunkowe  
  
-   Wprowadź wyrażenie warunkowe w **filtr, używając wyrażenia warunkowego** pole. Debuger ocenia wyrażenia dla każdego kontekstu wątku. Tylko wiersze, w których wartość jest `true` są wyświetlane.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Przewodnik: Debugowanie aplikacji C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
