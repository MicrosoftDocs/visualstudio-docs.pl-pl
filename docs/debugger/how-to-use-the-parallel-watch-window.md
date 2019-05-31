---
title: Ustawianie wyrażenia kontrolnego na zmiennych w równoległych wątków | Dokumentacja firmy Microsoft
ms.date: 04/25/2017
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6026ab6d0d59fb3a8f945e554fda26f10d98f952
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388471"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Ustawianie wyrażenia kontrolnego na zmiennych w równoległych wątków w programie Visual Studio (C#, Visual Basic, C++)
W oknie czujki równoległej może jednocześnie wyświetlać wartości, które zawiera jedno wyrażenie, w wielu wątkach. Każdy wiersz reprezentuje wątek, który jest uruchomiony w aplikacji, ale wątek może być reprezentowany w wielu wierszach. Dokładniej mówiąc każdy wiersz reprezentuje wywołanie funkcji, w których funkcja Podpis pasuje do funkcji w bieżącej ramki stosu. Można sortować, zmienić kolejność, Usuń i grupować elementy, które w kolumnach. Możesz Flaga, Usuń flagę, blokowanie (zawieszenie) i Odblokuj wątki (Wznów). Następujące kolumny są wyświetlane w **równoległego wyrażenia kontrolnego** okna:

- Kolumna flagi, w którym można oznaczyć wątek, który chcesz zwrócić szczególną uwagę.

- Bieżącej kolumny wątku, w której żółta strzałka wskazuje bieżący wątek (zielona strzałka z zakręconym ogonkiem wskazuje, czy innym niż bieżący wątek jest bieżący kontekst debugera).

- Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelków, zadania i wątku.

  > [!TIP]
  > Aby wyświetlić informacje o zadaniu w **równoległego wyrażenia kontrolnego** okna, należy najpierw otworzyć **zadań** okna.

- Pustą *Dodaj wyrażenie kontrolne* kolumn, w których można wprowadzić wyrażenia, aby obejrzeć.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Aby wyświetlić okno czujki równoległej

1. Ustaw punkt przerwania w kodzie.

2. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja do osiągnięcia punktu przerwania.

3. Na pasku menu wybierz **debugowania**, **Windows**, **równoległego wyrażenia kontrolnego**, a następnie wybierz Okno czujki. Możesz otworzyć maksymalnie cztery systemu windows.

### <a name="to-add-a-watch-expression"></a>Aby dodać wyrażenia kontrolnego

- Wybierz jedną z pustą *Dodaj wyrażenie kontrolne* kolumny, a następnie wprowadź wyrażenie czujki.

### <a name="to-flag-or-unflag-a-thread"></a>Flaga lub usuń flagę wątku

- Wybierz kolumny flag wiersza (pierwsza kolumna) lub Otwórz menu skrótów dla wątku i wybierz pozycję **flagi** lub **Unflag**.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki

- Wybierz **Pokaż tylko oflagowane** przycisk w lewym górnym rogu **równoległego wyrażenia kontrolnego** okna.

### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku

- Kliknij dwukrotnie kolumnę bieżącego wątku (druga kolumna). (Klawiatura: Zaznacz wiersz i naciśnij klawisz Enter).

### <a name="to-sort-a-column"></a>Aby posortować kolumnę

- Wybierz nagłówek kolumny.

### <a name="to-group-threads"></a>Grupa wątków

- Otwórz menu skrótów dla okno czujki równoległej, wybierz polecenie **Group By**, a następnie wybierz element odpowiednie podmenu.

### <a name="to-freeze-or-thaw-threads"></a>Na blokowanie lub odblokowywanie wątków

- Otwórz menu skrótów dla wiersza, a następnie wybierz **Freeze** lub **Odblokuj**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Aby wyeksportować dane w oknie czujki równoległej

- Wybierz **Otwórz w programie Excel** przycisk, a następnie wybierz **Otwórz w programie Excel** lub **Eksportuj do pliku CSV**.

### <a name="to-filter-by-a-boolean-expression"></a>Aby filtrować według wyrażenie warunkowe

- Wprowadź wyrażenie warunkowe w **filtr, używając wyrażenia warunkowego** pole. Debuger ocenia wyrażenia dla każdego kontekstu wątku. Tylko wiersze, w których wartość jest `true` są wyświetlane.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: Korzystanie z okna wątków procesora GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Przewodnik: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)