---
title: Wyświetlanie stosu wywołań w debugerze | Microsoft Docs
description: Użyj okna stosu wywołań, aby wyświetlić wywołania funkcji lub procedur, które obecnie znajdują się na stosie w programie Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/29/2018
ms.topic: how-to
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
ms.openlocfilehash: 206c79a47ec59e02206332d80d1afe935fb72bdc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150629"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Wyświetlanie stosu wywołań i korzystanie z okna stosu wywołań w debugerze

Za pomocą okna **stosu wywołań** można wyświetlić wywołania funkcji lub procedur, które są aktualnie na stosie. Okno **stos wywołań** pokazuje kolejność, w której metody i funkcje są wywoływane. Stos wywołań to dobry sposób, aby sprawdzić i zrozumieć przepływ wykonywania aplikacji.

Gdy [symbole debugowania](#bkmk_symbols) nie są dostępne dla części stosu wywołań, okno **stosu wywołań** może nie być w stanie wyświetlić poprawnych informacji dla tej części stosu wywołań, wyświetlając zamiast tego:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Okno **stosu wywołań** przypomina perspektywę debugowania w niektórych środowisk IDE, takich jak przezaćmienie.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od opisanych tutaj, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz pozycję **Importuj i Eksportuj ustawienia** w menu **Narzędzia** .  Zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Wyświetlanie stosu wywołań w debugerze

- Podczas debugowania, w menu **Debuguj** wybierz opcję **stos wywołań systemu Windows >**.

  ![Okno stosu wywołań](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Żółta strzałka określa ramkę stosu, w której znajduje się wskaźnik wykonania. Domyślnie informacje o tej ramce stosu są wyświetlane w oknach źródło, **lokalne**, **Autostart**, **Watch** i **demontaż** . Aby zmienić kontekst debugera na inną ramkę na stosie, [Przełącz się do innej ramki stosu](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Wyświetl kod niebędący użytkownikiem w oknie stosu wywołań

- Kliknij prawym przyciskiem myszy okno **stos wywołań** i wybierz polecenie **Pokaż kod zewnętrzny**.

Kod niebędący użytkownikiem jest dowolnym kodem, który nie jest wyświetlany, gdy [tylko mój kod](../debugger/just-my-code.md) jest włączona. W kodzie zarządzanym ramki kodu niezwiązane z użytkownikiem są domyślnie ukryte. Poniższy zapis występuje zamiast ramek kodu niebędących użytkownikami:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Przełącz do innej ramki stosu (Zmień kontekst debugera)

1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę stosu, której kod i dane chcesz wyświetlić.

    Można też kliknąć dwukrotnie ramkę w oknie **stosu wywołań** , aby przełączyć się do tej ramki.

2. Wybierz pozycję **Przełącz do ramki**.

     Zielona strzałka z ogonem klamrowym pojawia się obok wybranej ramki stosu. Wskaźnik wykonywania pozostaje w oryginalnej ramce, która nadal jest oznaczona żółtą strzałką. Jeśli wybierzesz pozycję **krok** lub **Kontynuuj** z menu **Debuguj** , wykonywanie będzie kontynuowane w pierwotnej ramce, a nie w wybranej ramce.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Wyświetlanie kodu źródłowego dla funkcji na stosie wywołań

- W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod źródłowy chcesz zobaczyć, i wybierz polecenie **Przejdź do kodu źródłowego**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Uruchom do określonej funkcji w oknie stosu wywołań

- W oknie **stos wywołań** zaznacz funkcję, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom do kursora**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Ustaw punkt przerwania w punkcie wyjścia wywołania funkcji

- Zobacz [Ustawianie punktu przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Wyświetlanie wywołań do lub z innego wątku

- Kliknij prawym przyciskiem myszy okno **stos wywołań** i wybierz pozycję **Dołącz wywołania do/z innych wątków**.

## <a name="visually-trace-the-call-stack"></a>Wizualne śledzenie stosu wywołań

W Visual Studio Enterprise (tylko) można wyświetlić mapy kodu dla stosu wywołań podczas debugowania.

- W oknie **stos wywołań** Otwórz menu skrótów. Wybierz pozycję **Pokaż stos wywołań na mapie kodu** (**Ctrl**  +  **SHIFT**  +  **`** ).

    Aby uzyskać więcej informacji, zobacz [Mapowanie metod w stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Pokaż stos wywołań na mapie kodu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Wyświetlanie kodu demontażu dla funkcji na stosie wywołań (C#, C++, Visual Basic, F #)

- W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod demontażu chcesz zobaczyć, i wybierz polecenie **Przejdź do demontażu**.

## <a name="change-the-optional-information-displayed"></a>Zmień wyświetlane informacje opcjonalne

- Kliknij prawym przyciskiem myszy w oknie **stos wywołań** i ustaw lub wyczyść opcję **Pokaż \<**_the information that you want_**>**.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Załaduj symbole dla modułu (C#, C++, Visual Basic, F #)

W oknie **stos wywołań** można załadować symbole debugowania dla kodu, który nie ma obecnie załadowanych symboli. Tymi symbolami mogą być symbole .NET lub systemowe pobrane z publicznych serwerów symboli firmy Microsoft lub symbole w ścieżce symboli na komputerze, który jest debugowany.

Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Aby załadować symbole

1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę stosu, dla której symbole nie są ładowane. Ramka będzie wyszarzona.

2. Wskaż **Załaduj symbole** , a następnie wybierz pozycję **serwery symboli firmy Microsoft** (jeśli są dostępne) lub przejdź do ścieżki symboli.

### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symbolu

1. W oknie **stos wywołań** wybierz pozycję **Ustawienia symboli** z menu skrótów.

     Zostanie otwarte okno dialogowe **Opcje** i zostanie wyświetlona strona **symbole** .

2. Wybierz pozycję **Ustawienia symboli**.

3. W oknie dialogowym **Opcje** kliknij ikonę folderu.

     W polu **lokalizacje pliku symboli (. pdb)** pojawia się kursor.

4. Wprowadź nazwę ścieżki katalogu do lokalizacji symboli na komputerze, który jest debugowany. W przypadku debugowania lokalnego i zdalnego jest to ścieżka na komputerze lokalnym.

5. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Opcje** .

## <a name="see-also"></a>Zobacz także

- [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Korzystanie z punktów przerwania](../debugger/using-breakpoints.md)