---
title: 'Instrukcje: Korzystanie z okna wątków GPU | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7b97c346cc933e14292fbb1198bfb69ecf59717
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696160"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Instrukcje: Korzystanie z okna wątków GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno wątków GPU można zbadać i Praca z wątkami, które są uruchomione w procesorze GPU w aplikacji, na którym wykonujesz debugowanie. Aby uzyskać więcej informacji na temat aplikacji działających na procesorze GPU, zobacz [Przegląd C++ AMP](https://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 Okno wątków GPU zawiera tabelę, w którym każdy wiersz reprezentuje zestaw wątków GPU, które mają takie same wartości we wszystkich kolumnach. Można sortować, zmienić kolejność, Usuń i grupowania elementów, które w kolumnach. Możesz Flaga, Usuń flagę, blokowanie (zawieszenie) i Odblokuj wątki (Wznów) z okna wątków GPU. Następujące kolumny są wyświetlane w oknie wątków GPU:  
  
- Kolumna flagi, w którym można oznaczyć wątek, który chcesz zwrócić szczególną uwagę.  
  
- Kolumna aktywnego wątku, w której żółta strzałka wskazuje aktywny wątek. Strzałka wskazuje wątek, w którym wykonanie przerwało pracę debugera.  
  
- **Liczba wątków** kolumny, która wyświetla liczbę wątków w tej samej lokalizacji.  
  
- **Wiersza** kolumny, która wyświetla wiersz kodu, w którym znajduje się każda grupa wątków.  
  
- **Adres** kolumny, która wyświetla adres instrukcji, w którym znajduje się każda grupa wątków. Domyślnie ta kolumna jest ukryta.  
  
- **Lokalizacji** kolumny, która jest lokalizacją w kodzie źródłowym.  
  
- **Stan** kolumny, która wskazuje, czy wątek aktywnych, zablokowane, nie jest uruchomiona lub ukończone.  
  
- **Kafelek** kolumny, która zawiera indeks kafelka dla wątków w wierszu.  
  
  Nagłówek tabeli pokazuje Kafelek i wątku są wyświetlane.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Aby wyświetlić okno wątków GPU  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
2. W **stron właściwości** okna dla projektu, w obszarze **właściwości konfiguracji**, wybierz **debugowanie**.  
  
3. W **debuger do uruchomienia** listy wybierz **lokalny debuger Windows**. W **typ debugera** listy wybierz **tylko GPU**. Musisz wybrać to przerwanie debugowania w punktach przerwania w kodzie, który działa na procesorze GPU.  
  
4. Wybierz **OK** przycisku.  
  
5. Ustaw punkt przerwania w kodzie procesora GPU.  
  
6. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja do osiągnięcia punktu przerwania.  
  
7. Jeden na pasku menu wybierz **debugowania**, **Windows**, **wątków GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Aby zmienić na inny wątek aktywny  
  
- Kliknij dwukrotnie kolumnę. (Klawiatura: Zaznacz wiersz i wybierz klawisz Enter).  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Do wyświetlania określonego fragmentu i wątku  
  
1. Wybierz **rozwiń przełącznik wątku** przycisku z okna wątków GPU.  
  
2. Wprowadź fragmentu i wątku wartości w polach tekstowych.  
  
3. Wybierz przycisk, który zawiera strzałkę znajdującą się na nim.  
  
### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumny  
  
- Otwórz menu skrótów okna wątków GPU, wybierz **kolumn**, a następnie wybierz kolumnę, którą chcesz wyświetlić lub ukryć.  
  
### <a name="to-sort-by-a-column"></a>Aby sortować według kolumny  
  
- Wybierz nagłówek kolumny.  
  
### <a name="to-group-threads"></a>Grupa wątków  
  
- Otwórz menu skrótów okna wątków GPU, wybierz **Group By**, a następnie wybierz jedną z nazw kolumn wyświetlane. Wybierz **Brak** rozgrupować wątków.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Na blokowanie lub odblokowywanie wątków wiersz  
  
- Otwórz menu skrótów dla wiersza, a następnie wybierz **Freeze** lub **Odblokuj**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Aby Flagowanie wiersz wątków lub  
  
- Wybierz kolumnę flagę wątku, lub Otwórz menu skrótów dla wątku i wybierz **flagi** lub **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
- Kliknij przycisk flagi w okno wątków GPU.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Przewodnik: debugowanie aplikacji C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
