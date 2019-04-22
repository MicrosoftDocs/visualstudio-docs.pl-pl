---
title: Debugowanie aplikacji wielowątkowych
description: Debugowanie za pomocą okna wątki i narzędzi debugowania lokalizacji, w programie Visual Studio
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3a87fd0480727a524b36ab209f5126b0f996c30
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790800"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Przewodnik: Debugowanie aplikacji wielowątkowych, za pomocą okna wątki (C#, Visual Basic, C++)

Kilka elementów interfejsu użytkownika programu Visual Studio ułatwiają debugowanie aplikacji wielowątkowych. W tym artykule przedstawiono wielowątkowe funkcji debugowania, w oknie edytora kodu **Lokalizacja debugowania** narzędzi i **wątków** okna. Aby uzyskać informacje o innych narzędzi do debugowania aplikacji wielowątkowych, zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).

Wykonanie kroków tego samouczka zajmuje tylko kilka minut, a także pozwala zaznajomić się z podstawowe informacje dotyczące debugowania aplikacji wielowątkowych.

## <a name="create-a-multithreaded-app-project"></a>Tworzenie projektu aplikacji wielowątkowych

Utwórz następujący projekt aplikacja wielowątkowa do użycia w ramach tego samouczka:

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **konsoli** (lub **c ++**), wybierz **szablony**, a następnie:

    - Aby uzyskać C#, wybierz **Utwórz nowy projekt aplikacji konsoli (.NET Framework)** dla C#. W oknie dialogowym wybierz **Utwórz**.
    - Dla języka C++, wybierz **Tworzenie nowego projektu aplikacji Konsolowej**. W oknie dialogowym wybierz **Utwórz**.

    Następnie wpisz nazwę, takich jak **MyThreadWalkthroughApp** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okna dialogowego pole, wybierz następujące opcje:
    - Dla C# aplikacji, w obszarze **Visual C#** , wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET Framework)**.
    - Dla aplikacji w języku C++ w obszarze **Visual C++**, wybierz **pulpitu Windows**,, a następnie wybierz **aplikacji konsoli Windows**.

    Następnie wpisz nazwę, takich jak **MyThreadWalkthroughApp** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz **aplikacja Konsolowa** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** lub **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj**.

    Nowy projekt, który pojawia się w **Eksploratora rozwiązań**, oraz plik źródłowy o nazwie *Program.cs* lub *MyThreadWalkthroughApp.cpp* zostanie otwarty w oknie kodu źródłowego.

1. Zastąp kod w pliku źródłowym, za pomocą C# lub C++ przykładowy kod z [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).

1. Wybierz **pliku** > **Zapisz wszystko**.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Znajdź następujące wiersze w kodzie źródłowym:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Ustaw punkt przerwania na `Console.WriteLine();` wiersza, klikając na lewym marginesie lub zaznaczając wiersz i naciskając klawisz **F9**.

   Punkt przerwania pojawia się jako czerwone kółko na lewym marginesie obok wiersza kodu.

1. Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij **F5**.

   Aplikacja jest uruchamiana w trybie debugowania i zatrzymuje się w punkcie przerwania.

1. W trybie przerwania, otwórz **wątków** okna, wybierając **debugowania** > **Windows** > **wątków**. Musi być w sesji debugowania, aby otworzyć, lub zobacz **wątków** i innych oknach debugowania.

## <a name="examine-thread-markers"></a>Sprawdź znaczników wątków

1. W kodzie źródłowym, zlokalizuj `Console.WriteLine();` wiersza.

   1. Kliknij prawym przyciskiem myszy **wątków** okna, a następnie wybierz **Pokaż wątki w źródle** ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") z menu.

   Oprawę obok kodu źródłowego wiersz wyświetla teraz *znacznika wątku* ikonę ![znacznika wątku](../debugger/media/dbg-thread-marker.png "znacznika wątku"). Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji. Jeśli w lokalizacji, ma więcej niż jeden wątek zatrzymania ![wielu wątków](../debugger/media/dbg-multithreaded-show-threads.png "wielu wątków") pojawi się ikona.

1. Umieść wskaźnik myszy nad znacznika wątku. Etykietki danych zostanie wyświetlony numer identyfikacyjny nazwy i wątku dla zatrzymanego wątku lub wątków. Nazwy wątków może być `<No Name>`.

   >[!TIP]
   >Aby ułatwić identyfikację pustego wątki, można zmienić nazwy w **wątków** okna. Kliknij prawym przyciskiem myszy wątku, a następnie wybierz pozycję **Zmień nazwę**.

1. Kliknij prawym przyciskiem myszy znacznika wątku w kodzie źródłowym, aby wyświetlić dostępne opcje w menu skrótów.

## <a name="flag-and-unflag-threads"></a>Oflagowanie i usuwanie oflagowania wątków

Może Flaga wątków do śledzenia wątków, które chcesz zwrócić szczególną uwagę.

Oflagowanie i usuwanie oflagowania wątków z Edytor kodu źródłowego lub **wątków** okna. Wybierz, czy mają być wyświetlane tylko oflagowane wątki lub wszystkie wątki z **Lokalizacja debugowania** lub **wątków** paski narzędzi okna. Wybory dokonane z dowolnego miejsca i wpływają na wszystkie lokalizacje.

### <a name="flag-and-unflag-threads-in-source-code"></a>Oflagowanie i usuwanie oflagowania wątków w kodzie źródłowym

1. Otwórz **Lokalizacja debugowania** narzędzi, wybierając **widoku** > **pasków narzędzi** > **Lokalizacja debugowania**. Możesz również kliknąć prawym przyciskiem myszy obszar paska narzędzi i wybierz **Lokalizacja debugowania**.

1. **Lokalizacja debugowania** narzędzi ma trzy pola: **Proces**, **wątku**, i **ramki stosu**. Lista rozwijana **wątku** listy i zwróć uwagę, jak wiele wątków są. W **wątku** listy aktualnie wykonywany wątek jest oznaczony za **>** symboli.

1. W oknie kodu źródłowego wskaźnik myszy na ikonie znacznika wątku, na marginesie, a następnie wybierz ikonę flagi (lub jedną z ikon flagi pusta) w DataTip. Ikony flagi zmieni kolor na czerwony.

   Również kliknięciu prawym przyciskiem myszy ikonę znacznika wątku, wskaż polecenie **flagi**, a następnie wybierz wątek mógł oflagować z menu skrótów.

1. Na **Lokalizacja debugowania** narzędzi, wybierz opcję **Pokaż tylko oflagowane wątki** ikonę ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "Pokaż oflagowane wątki"), po prawej stronie **wątku** pola. Ikona jest wyszarzona, chyba że są oznaczane jeden lub więcej wątków.

   Tylko wątków oflagowanych jest teraz wyświetlany w **wątku** listy rozwijanej na pasku narzędzi. Aby ponownie wyświetlić wszystkie wątki, wybierz **Pokaż tylko oflagowane wątki** ponownie ikonę.

   >[!TIP]
   >Po flagą niektóre wątki, można umieścić kursor w edytorze kodu, kliknij prawym przyciskiem myszy i wybierz **Uruchom oflagowane wątki do kursora**. Upewnij się, że wybierz kod wszystkich wątków oflagowanych skontaktuje. **Uruchom oflagowane wątki do kursora** wstrzyma wątków na wybrany wiersz kodu, dzięki czemu łatwiej jest kontrolować kolejność wykonywania przez [zawiesza się i odblokowania wątków](#bkmk_freeze).

1. Aby włączyć/wyłączyć oflagowanych lub bez flagi stanu aktualnie wykonywany wątek, wybierz pojedynczej flagi **Przełącz bieżący wątek Oflagowani stan** przycisku paska narzędzi po lewej stronie **Pokaż tylko oflagowane wątki** przycisk. Flagowanie bieżącego wątku jest przydatne do lokalizowania bieżącego wątku, gdy są wyświetlane są tylko oflagowane wątki.

1. Aby Usuń flagę wątku, umieść kursor nad znacznika wątku w kodzie źródłowym, a następnie wybierz ikonę czerwona flaga, aby wyczyścić, lub kliknij prawym przyciskiem myszy znacznika wątku i wybrać **Unflag**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Oflagowanie i usuwanie oflagowania wątków z okna wątków

W **wątków** oknie oflagowane wątki mają czerwona flaga ikony obok nich, podczas bez flagi wątków, jeśli wyświetlony, ma pusty ikon.

![Okno wątków](../debugger/media/dbg-threads-window.png "okna wątków")

Wybierz ikonę flagi, aby zmienić stan wątku oflagowanych lub bez flagi, w zależności od bieżącego stanu.

Możesz również kliknąć prawym przyciskiem myszy linię i wybierz **flagi**, **Unflag**, lub **Usuń flagę ze wszystkich wątków** z menu skrótów.

**Wątków** ma również pasek narzędzi okna **Pokaż wątki tylko oflagowane** przycisku, który jest righthand, jedną z ikon dwie flagi. Działa tak samo, jak przycisk na **Lokalizacja debugowania** narzędzi i albo przycisk kontroluje wyświetlanie w obu lokalizacjach.

### <a name="other-threads-window-features"></a>Inne funkcje okna wątków

W **wątków** okna, wybierz nagłówek dowolnej kolumny, aby posortować wątki według tej kolumny. Wybierz ponownie, aby odwrócić porządek sortowania. Jeżeli wszystkie wątki są wyświetlane, wybierając kolumnę ikonę flagi sortuje wątki oflagowane lub bez flagi stanu.

Druga kolumna **wątków** okno (z bez nagłówka) jest **bieżący wątek** kolumny. Żółta strzałka w tej kolumnie oznacza bieżący punkt wykonania.

**Lokalizacji** kolumna pokazuje, w którym każdy wątek pojawia się w kodzie źródłowym. Wybierz strzałkę obok rozwiń pola **lokalizacji** wpisu lub Najedź kursorem wpis, aby wyświetlić stos wywołań częściowe dla tego wątku.

>[!TIP]
>Graficzne przedstawienie stosy wywołań dla wątków, można użyć [stosów równoległych](../debugger/using-the-parallel-stacks-window.md) okna. Aby otworzyć okno, podczas debugowania, wybierz pozycję **debugowania**> **Windows** > **stosów równoległych**.

Oprócz **flagi**, **Unflag**, i **Usuń flagę ze wszystkich wątków**, kliknij prawym przyciskiem myszy menu kontekstowe dla **wątku** ma elementy okna:

- **Pokaż wątki w źródle** przycisku.
- **Wyświetlanie szesnastkowe**, jakie zmiany **identyfikator wątku**s w **wątków** okna dziesiętnych formacie szesnastkowym.
- [Przełącz do wątku](#switch-to-another-thread), który natychmiast zmienia wykonania na tym wątku.
- **Zmień nazwę**, które pozwala zmienić nazwę wątku.
- [Blokowanie i odblokowywanie](#bkmk_freeze) poleceń.

## <a name="bkmk_freeze"></a> Zablokuj i Odblokuj wątek wykonywania

Można Zablokuj i Odblokuj, lub wstrzymywanie i wznawianie wątków, aby kontrolować kolejność, w którym wątki wykonywania pracy. Zawiesza się i odblokowania wątków może pomóc rozwiązać problemy z współbieżności, takich jak zakleszczenia i wyścigu.

> [!TIP]
> Aby skorzystać z jednego wątku bez zawiesza innych wątków, który również jest to typowy scenariusz debugowania, zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Zablokuj i Odblokuj wątki:**

1. W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie wybierz pozycję **Freeze**. A **Wstrzymaj** ikonę **bieżącego wątku** kolumna wskazuje, że wątek jest zablokowane.

1. Wybierz **kolumn** w **wątków** pasek narzędzi okna, a następnie wybierz **zawieszone liczba** do wyświetlenia **zawieszone liczba** kolumny. Liczba wstrzymanych wartość zablokowanego wątku jest **1**.

1. Kliknij prawym przyciskiem myszy zablokowanego wątku, a następnie wybierz pozycję **Odblokuj**.

   **Wstrzymaj** ikona zniknie i **zawieszone liczba** zmiany wartości na **0**.

## <a name="switch-to-another-thread"></a>Przełączanie na inny wątek

Może zostać wyświetlony **aplikacja jest w trybie przerwania** okna przy próbie przełączenia do innego wątku. W tym oknie informuje, że wątek nie ma żadnego kodu, który może wyświetlać bieżący debuger. Na przykład może być debugowanie kodu zarządzanego, ale wątek jest kodu natywnego. Okno sugestie dotyczące rozwiązania tego problemu.

**Aby przełączyć się do innego wątku:**

1. W **wątków** okna, Zanotuj identyfikator bieżącego wątku, czyli wątku z żółtą strzałką w **bieżącego wątku** kolumny. Należy wrócić do tego wątku, aby kontynuować swojej aplikacji.

1. Kliknij prawym przyciskiem myszy w innym wątku, a następnie wybierz pozycję **Przełącz do wątku** z menu kontekstowego.

1. Sprawdź, czy lokalizacja żółta strzałka została zmieniona w **wątków** okna. Oryginalny bieżącego znacznika wątku pozostaje też obecna, jako kontur.

   Spójrz na etykietce narzędzia znacznika wątku w edytorze kodu źródłowego i na liście w **wątku** menu rozwijane **Lokalizacja debugowania** paska narzędzi. Sprawdź, czy bieżący wątek został zmieniony istnieje.

1. Na **Lokalizacja debugowania** narzędzi, wybierz inny wątek z **wątku** listy. Należy pamiętać, że bieżący wątek zmienia się w innych lokalizacjach również.

1. W edytorze kodu źródłowego, kliknij prawym przyciskiem myszy znacznika wątku, wskaż opcję **Przełącz do wątku**, a następnie wybierz inny wątek z listy. Sprawdź, czy bieżący wątek zmiany we wszystkich trzech lokalizacjach.

Za pomocą znacznika wątku w kodzie źródłowym można przełączyć tylko na wątki, które zostały zatrzymane w tej lokalizacji. Za pomocą **wątków** okna i **Lokalizacja debugowania** narzędzi można przełączyć na żadnym z wątków.

Teraz znasz już podstawowe informacje dotyczące debugowania aplikacji wielowątkowych. Możesz obserwować, Flaga i Usuń flagę i Zablokuj i Odblokuj wątki przy użyciu **wątków** oknie **wątku** listy w **Lokalizacja debugowania** paska narzędzi lub znaczniki wątków w Edytor kodu źródłowego.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: Przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
