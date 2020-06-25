---
title: Ustaw obserwację zmiennych w wątkach równoległych | Microsoft Docs
ms.date: 04/25/2017
ms.topic: how-to
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
ms.openlocfilehash: 9fb0d5ac60ea5ab89b02a624488b5df4f8a7164b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348629"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Ustaw kontrolkę na zmienne w wątkach równoległych w programie Visual Studio (C#, Visual Basic, C++)
W okno wyrażeń kontrolnych równoległym można jednocześnie wyświetlić wartości, które są przechowywane w jednym wyrażeniu na wielu wątkach. Każdy wiersz reprezentuje wątek, który jest uruchomiony w aplikacji, ale wątek może być reprezentowany w wielu wierszach. Dokładniej mówiąc, każdy wiersz reprezentuje wywołanie funkcji, którego sygnatura funkcji dopasowuje funkcję w bieżącej klatce stosu. Elementy, które znajdują się w kolumnach, można sortować, zmienić ich kolejność, usunąć i zgrupować. Wątki można flagować, anulować flagować, zamrażać (wstrzymywać) i rozmrażać (wznawiać). W oknie **czujki równoległej** są wyświetlane następujące kolumny:

- Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę.

- Kolumna bieżącego wątku, w której żółta strzałka wskazuje bieżący wątek (zielona strzałka z ogonem klamrowym wskazuje, że wątek inny niż bieżący ma bieżący kontekst debugera).

- Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelek, zadanie i wątek.

  > [!TIP]
  > Aby wyświetlić informacje o zadaniu w oknie **czujki równoległej** , należy najpierw otworzyć okno **zadania** .

- Puste *Dodaj kolumny czujki* , w której można wprowadzać wyrażenia do obejrzenia.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Aby wyświetlić okno wyrażeń kontrolnych równoległy

1. Ustaw punkt przerwania w kodzie.

2. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja osiągnie punkt przerwania.

3. Na pasku menu wybierz kolejno opcje **Debuguj**, **Windows**i **Parallel Watch**, a następnie okno Czujka. Możesz otworzyć maksymalnie cztery okna.

### <a name="to-add-a-watch-expression"></a>Aby dodać wyrażenie czujki

- Wybierz jedną z pustych opcji *Dodaj* kolumny, a następnie wprowadź wyrażenie kontrolne.

### <a name="to-flag-or-unflag-a-thread"></a>Aby oflagować lub Usuń flagę wątku

- Wybierz kolumnę flag dla wiersza (pierwszej kolumny) lub Otwórz menu skrótów dla wątku, a następnie wybierz **flagę** lub Usuń **flagę**.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki

- Wybierz przycisk **Pokaż tylko Oflagowane** w lewym górnym rogu okna **czujki równoległej** .

### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku

- Kliknij dwukrotnie kolumnę bieżący wątek (druga kolumna). (Klawiatura: zaznacz wiersz i naciśnij klawisz ENTER).

### <a name="to-sort-a-column"></a>Aby posortować kolumnę

- Wybierz nagłówek kolumny.

### <a name="to-group-threads"></a>Do grup wątków

- Otwórz menu skrótów dla okno wyrażeń kontrolnych równoległych, wybierz pozycję **Grupuj według**, a następnie wybierz odpowiedni element podmenu.

### <a name="to-freeze-or-thaw-threads"></a>Aby zablokować lub odblokować wątki

- Otwórz menu skrótów dla wiersza, a następnie wybierz polecenie **Zablokuj** lub **rozmrażaj**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Aby wyeksportować dane w okno wyrażeń kontrolnych równoległym

- Wybierz przycisk **Otwórz w programie Excel** , a następnie wybierz **Otwórz w programie Excel** lub **Eksportuj do pliku CSV**.

### <a name="to-filter-by-a-boolean-expression"></a>Aby odfiltrować według wyrażenia logicznego

- Wprowadź wyrażenie logiczne w polu **Filtruj według wartości logicznej** . Debuger oblicza wyrażenie dla każdego kontekstu wątku. Wyświetlane są tylko wiersze, w których jest `true` wyświetlana wartość.

## <a name="see-also"></a>Zobacz też
- [Debuguj wielowątkowe aplikacje](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Przewodnik: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)