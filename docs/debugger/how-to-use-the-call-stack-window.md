---
title: Wyświetl stos wywołań w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2673ed9a69a80b2e9ab9275ff54909e33e4434f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906363"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Wyświetl stos wywołań i korzystanie z okna stosu wywołań w debugerze

Za pomocą **stos wywołań** okna, można wyświetlić wywołania funkcji lub procedur, które obecnie znajdują się w stosie. **Stos wywołań** okno pokazuje kolejność, w którym są wprowadzenie wywoływane metody i funkcje. Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

Gdy [symboli debugowania](#bkmk_symbols) nie są dostępne dla części stosu wywołań, **stos wywołań** okna może nie móc wyświetlić poprawnych informacji w tej części stosu wywołań, zamiast wyświetlania:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w tym miejscu, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz pozycję **Import i eksport ustawień** na **narzędzia** menu.  Zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Wyświetl stos wywołań, znajduje się w debugerze

- Podczas debugowania w **debugowania** menu, wybierz opcję **Windows > stos wywołań**.

  ![Okno stosu wywołań](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Żółta strzałka identyfikuje ramkę stosu, w którym aktualnie znajduje się wskaźnik wykonania. Domyślnie tej ramki stosu informacje są wyświetlane w źródle, **lokalne**, **Autos**, **Obejrzyj**, i **dezasemblacji** systemu windows. Aby zmienić kontekst debugera do innej ramki na stosie, [przełączyć się do innej ramki stosu](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Wyświetl kod niezwiązany z użytkownikiem w oknie stosu wywołań

- Kliknij prawym przyciskiem myszy **stos wywołań** okna, a następnie wybierz pozycję **Pokaż kod zewnętrzny**.

Kod niezwiązany z użytkownikiem jest wszelki kod, który nie jest wyświetlany podczas [tylko mój kod](../debugger/just-my-code.md) jest włączona. W kodzie zarządzanym ramki kodu niepochodzącego od użytkownika są domyślnie ukryte. Zamiast ramki kodu niepochodzącego od użytkownika pojawia się następujący zapis:

`[<External Code>]`

## <a name="bkmk_switch"></a> Przełącz się do innej ramki stosu (Zmień kontekst debugera)

1. W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramek stosu, której kod i dane, które chcesz wyświetlić.

    Alternatywnie możesz kliknąć dwukrotnie ramki w **stos wywołań** okna, aby przełączyć się do tej ramki.

2. Wybierz **Przełącz do ramki**.

     Zielona strzałka z zakręconym ogonkiem pojawia się obok wybranej przez użytkownika ramki stosu. Wskaźnik wykonania pozostaje w pierwotnej ramce, która nadal jest oznaczona żółtą strzałką. Jeśli wybierzesz **kroku** lub **Kontynuuj** z **debugowania** menu, wykonywanie będzie kontynuowane w pierwotnej ramce, nie ramce wybranej.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Wyświetlanie kodu źródłowego dla funkcji na stosie wywołań

- W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcję, której kod źródłowy chcesz wyświetlić i wybierz **przejdź do kodu źródłowego**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Uruchom określoną funkcję z okna stosu wywołań

- W **stos wywołań** okna, wybierz funkcję, kliknij prawym przyciskiem myszy, a następnie wybierz **Uruchom do kursora**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Ustaw punkt przerwania w punkcie Zakończ wywołania funkcji

- Zobacz [Ustaw punkt przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Wyświetlić wywołania do lub z innego wątku

- Kliknij prawym przyciskiem myszy **stos wywołań** okna, a następnie wybierz pozycję **obejmują wywołania do / z innych wątków**.

## <a name="visually-trace-the-call-stack"></a>Wizualnie śledzić stos wywołań

W programie Visual Studio Enterprise (tylko) możesz wyświetlić mapy kodu dla stosu wywołań podczas debugowania.

- W **stos wywołań** okna, otwórz menu skrótów. Wybierz **Pokaż stos wywołań na mapie kodu** (**Ctrl** + **Shift** + **`**).

    Aby uzyskać więcej informacji, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Pokaż stos wywołań na mapie kodu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Wyświetlanie kodu dezasemblacji dla funkcji na stosie wywołań (C#, C++, Visual Basic F#)

- W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcję, której kod demnotażu chcesz wyświetlić i wybierz **przejdź do demontażu**.

## <a name="change-the-optional-information-displayed"></a>Zmienić wyświetlane informacje opcjonalne

- Kliknij prawym przyciskiem myszy **stos wywołań** okna i zestawu lub wyczyść **Pokaż \<**  _informacje, które mają_ **>**.

## <a name="bkmk_symbols"></a> Ładowanie symboli dla modułu (C#, C++, Visual Basic F#)

W **stos wywołań** okna, możesz załadować symbole debugowania dla kodu, który nie ma obecnie załadowanych symboli. Te symbole mogą być .NET Framework lub symbole systemu, które zostały pobrane z serwerów symboli publicznych firmy Microsoft lub symbolami w ścieżce symboli na komputerze, na którym wykonujesz debugowanie.

Zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Aby załadować symbole

1. W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramkę stosu, dla której symbole nie są ładowane. Ramki będą wyszarzone.

2. Wskaż **załadować symbole** , a następnie wybierz **serwery symboli firmy Microsoft** (jeśli jest dostępny), lub wyszukaj ścieżkę symboli.

### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symboli

1. W **stos wywołań** oknie Wybierz **ustawienia symboli** z menu skrótów.

     **Opcje** zostanie otwarte okno dialogowe i **symbole** zostanie wyświetlona strona.

2. Wybierz **ustawienia symboli**.

3. W **opcje** okna dialogowego kliknij ikonę folderu.

     W **symboli (.pdb) lokalizacji** polu, pojawi się kursor.

4. Wprowadź nazwę ścieżki katalogu do lokalizacji symbolu na komputerze, na którym wykonujesz debugowanie. Lokalne i zdalne debugowanie, jest to ścieżka na komputerze lokalnym.

5. Wybierz **OK** zamknąć **opcje** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Określanie plików symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Używanie punktów przerwania](../debugger/using-breakpoints.md)