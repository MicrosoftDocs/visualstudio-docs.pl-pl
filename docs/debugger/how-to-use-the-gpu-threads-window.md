---
title: Wyświetlanie wątków GPU w debugerze | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbb49a1017fb0bc65300f3c16050db4954e1103
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348720"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Instrukcje: korzystanie z okna wątków GPU (C++)
W oknie wątki GPU można przeanalizować i pracować z wątkami uruchomionymi na procesorze GPU w debugowanej aplikacji. Aby uzyskać więcej informacji o aplikacjach uruchamianych na procesorze GPU, zobacz [C++ amp Omówienie](/cpp/parallel/amp/cpp-amp-overview).

 Okno wątki GPU zawiera tabelę, w której każdy wiersz reprezentuje zestaw wątków procesora GPU, które mają te same wartości we wszystkich kolumnach. Można sortować, zmienić kolejność, usuwać i grupować elementy, które znajdują się w kolumnach. Wątki z okna wątków GPU umożliwiają Flagowanie, usuwanie flag, blokowanie (Wstrzymywanie) i odblokowywanie (wznawianie). W oknie wątki GPU są wyświetlane następujące kolumny:

- Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę.

- Kolumna bieżącego wątku, w której żółta strzałka wskazuje bieżący wątek.

- Kolumna **Liczba wątków** , która wyświetla liczbę wątków w tej samej lokalizacji.

- Kolumna **wiersz** , w której jest wyświetlany wiersz kodu, w którym znajduje się każda grupa wątków.

- Kolumna **adres** , w której jest wyświetlany adres instrukcji, w której znajduje się każda grupa wątków. Domyślnie ta kolumna jest ukryta.

- Kolumna **lokalizacji** , która jest lokalizacją w kodzie źródłowym.

- Kolumna **stan** , która pokazuje, czy wątek jest aktywny, zablokowany, nie uruchomiono lub został ukończony.

- Kolumna **kafelka** , która pokazuje indeks kafelków dla wątków w wierszu.

  Nagłówek tabeli pokazuje wyświetlany kafelek i wątek.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>Aby wyświetlić okno wątków GPU

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

2. W oknie **strony właściwości** dla projektu, w obszarze **Właściwości konfiguracji**wybierz **debugowanie**.

3. Na liście **debuger do uruchomienia** wybierz pozycję **lokalny debuger systemu Windows**. Na liście **Typ debugera** wybierz pozycję **tylko procesor GPU**. Musisz wybrać ten debuger, aby przerwać w punkcie przerwania w kodzie, który jest uruchamiany na procesorze GPU.

4. Wybierz przycisk **OK** .

5. Ustaw punkt przerwania w kodzie procesora GPU.

6. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja osiągnie punkt przerwania.

7. Na pasku menu wybierz kolejno opcje **Debuguj**, **Windows**i **GPU**.

### <a name="to-switch-to-a-different-thread"></a>Aby przełączyć się do innego wątku

- Kliknij dwukrotnie kolumnę. (Klawiatura: zaznacz wiersz i wybierz klawisz ENTER).

### <a name="to-display-a-particular-tile-and-thread"></a>Aby wyświetlić określony kafelek i wątek

1. Wybierz przycisk **rozszerzanie wątku** w oknie wątki GPU.

2. Wprowadź wartości kafelka i wątku w polach tekstowych.

3. Wybierz przycisk, który ma strzałkę na nim.

### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumnę

- Otwórz menu skrótów okna wątki GPU, wybierz **kolumny**, a następnie wybierz kolumnę, która ma być wyświetlana lub ukryta.

### <a name="to-sort-by-a-column"></a>Aby posortować według kolumny

- Wybierz nagłówek kolumny.

### <a name="to-group-threads"></a>Do grup wątków

- Otwórz menu skrótów okna wątków GPU, wybierz pozycję **Grupuj według**, a następnie wybierz jedną z wyświetlanych nazw kolumn. Wybierz **Brak** , aby rozgrupować wątki.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Aby zablokować lub odblokować wiersz wątków

- Otwórz menu skrótów dla wiersza, a następnie wybierz polecenie **Zablokuj** lub **rozmrażaj**.

### <a name="to-flag-or-unflag-a-row-of-threads"></a>Aby oflagować lub Usuń flagę wiersza wątków

- Wybierz kolumnę flag dla wątku lub Otwórz menu skrótów dla wątku, a następnie wybierz **flagę** lub Usuń **flagę**.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki

- Wybierz przycisk flagi w oknie wątki GPU.

## <a name="see-also"></a>Zobacz też
- [Debuguj wielowątkowe aplikacje](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: korzystanie z okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md)
- [Przewodnik: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)