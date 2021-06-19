---
title: Wyświetlanie stosu wywołań w debugerze | Microsoft Docs
description: Okno Stos wywołań umożliwia wyświetlenie wywołań funkcji lub procedur, które znajdują się obecnie na stosie w Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e905a509443cd5fd30e860a887dd895c5ee21a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387479"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Wyświetlanie stosu wywołań i korzystanie z okna stosu wywołań w debugerze

Za pomocą **okna Stos** wywołań można wyświetlić wywołania funkcji lub procedury, które są obecnie w stosie. Okno **Stos wywołań** pokazuje kolejność wywoływania metod i funkcji. Stos wywołań to dobry sposób na zbadanie i zrozumienie przepływu wykonywania aplikacji.

Gdy [symbole debugowania](#bkmk_symbols) nie są dostępne dla  części stosu wywołań, okno stosu wywołań może nie być w stanie wyświetlić prawidłowych informacji dla tej części stosu wywołań, wyświetlając zamiast tego:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Okno **stosu wywołań jest** podobne do perspektywy debugowania w niektórych środowiskach PROJEKTOWYCH, takich jak Eclipse.

> [!NOTE]
> Wyświetlane okna dialogowe i polecenia menu mogą różnić się od opisanych tutaj, w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, wybierz pozycję **Importuj i eksportuj ustawienia** **w** menu Narzędzia.  Zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Wyświetlanie stosu wywołań w debugerze

- Podczas debugowania w menu **Debugowanie** wybierz pozycję **Windows > stos wywołań**.

  ![Okno stosu wywołań](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Żółta strzałka identyfikuje ramkę stosu, w której znajduje się obecnie wskaźnik wykonywania. Domyślnie informacje o ramce stosu są wyświetlane w oknach źródła, **locals,** **autos,** **watch** **i dezemberaty.** Aby zmienić kontekst debugera na inną ramkę na stosie, [przełącz się na inną ramkę stosu](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Wyświetlanie kodu bez użytkownika w oknie stosu wywołań

- Kliknij prawym przyciskiem myszy okno **Stos wywołań** i wybierz polecenie **Pokaż kod zewnętrzny**.

Kod niebędący użytkownikiem to dowolny kod, który nie jest wyświetlany [Tylko mój kod](../debugger/just-my-code.md) jest włączony. W kodzie zarządzanym ramki kodu inne niż użytkownika są domyślnie ukryte. W miejsce ramek kodu innych niż ramki kodu użytkownika jest wyświetlana następująca notacja:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Przełącz się na inną ramkę stosu (zmień kontekst debugera)

1. W **oknie Stos wywołań** kliknij prawym przyciskiem myszy ramkę stosu, której kod i dane chcesz wyświetlić.

    Możesz też kliknąć dwukrotnie ramkę w oknie **stosu** wywołań, aby przełączyć się do tej ramki.

2. Wybierz **pozycję Przełącz na ramkę**.

     Obok wybranej ramki stosu zostanie wyświetlona zielona strzałka ze zwiniętym ogonem. Wskaźnik wykonania pozostaje w oryginalnej ramce, która nadal jest oznaczona żółtą strzałką. Jeśli wybierzesz **pozycję Krok** **lub** Kontynuuj z menu **Debugowanie,** wykonywanie będzie kontynuowane w oryginalnej ramce, a nie w wybranej ramce.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Wyświetlanie kodu źródłowego funkcji na stosie wywołań

- W **oknie Stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod źródłowy chcesz wyświetlić, a następnie wybierz pozycję **Przejdź do kodu źródłowego**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Uruchamianie do określonej funkcji w oknie stosu wywołań

- W **oknie Stos wywołań** wybierz funkcję, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom do kursora**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Ustawianie punktu przerwania w punkcie wyjścia wywołania funkcji

- Zobacz [Ustawianie punktu przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Wyświetlanie wywołań do lub z innego wątku

- Kliknij prawym przyciskiem myszy okno **Stos wywołań** i wybierz **pozycję Uwzględnij wywołania do/z innych wątków**.

## <a name="visually-trace-the-call-stack"></a>Wizualne śledzenie stosu wywołań

W Visual Studio Enterprise (tylko) można wyświetlać mapy kodu dla stosu wywołań podczas debugowania.

- W **oknie Stos** wywołań otwórz menu skrótów. Wybierz pozycję **Pokaż stos wywołań na mapie kodu** **(Ctrl**  +    +  **`** Shift).

    Aby uzyskać więcej informacji, zobacz [Mapowanie metod na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Pokazywanie stosu wywołań na mapie kodu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Wyświetlanie kodu desembedżu dla funkcji w stosie wywołań (C#, C++, Visual Basic, F#)

- W **oknie Stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod dezmisji chcesz wyświetlić, i wybierz polecenie **Przejdź do dezembrację**.

## <a name="change-the-optional-information-displayed"></a>Zmienianie wyświetlanych opcjonalnych informacji

- Kliknij prawym przyciskiem myszy w **oknie Stos wywołań** i ustaw lub wyczyść pole **\<**_the information that you want_**> pokaż**.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Ładowanie symboli dla modułu (C#, C++, Visual Basic, F#)

W **oknie Stos** wywołań można załadować symbole debugowania dla kodu, który obecnie nie ma załadowanych symboli. Te symbole mogą być symbolami platformy .NET lub systemami pobranymi z publicznych serwerów symboli firmy Microsoft lub symbolami w ścieżce symboli na komputerze, który jest debugowania.

Zobacz [Temat Specify symbol (.pdb) and source files (Określanie plików symboli (.pdb) i plików źródłowych).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

### <a name="to-load-symbols"></a>Aby załadować symbole

1. W **oknie Stos wywołań** kliknij prawym przyciskiem myszy ramkę stosu, dla której symbole nie są ładowane. Ramka będzie wygaszona.

2. Wskaż polecenie **Załaduj** symbole, a następnie wybierz **pozycję Serwery symboli firmy Microsoft** (jeśli są dostępne) lub przejdź do ścieżki symboli.

### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symboli

1. W **oknie Stos wywołań** wybierz pozycję **Ustawienia symboli** z menu skrótów.

     Zostanie **otwarte** okno dialogowe Opcje i zostanie **wyświetlona** strona Symbole.

2. Wybierz **pozycję Ustawienia symboli.**

3. W **oknie dialogowym** Opcje kliknij ikonę Folder.

     W **polu Lokalizacje pliku symboli (.pdb)** pojawi się kursor.

4. Wprowadź nazwę ścieżki katalogu do lokalizacji symbolu na debugowaniu komputera. W przypadku debugowania lokalnego i zdalnego jest to ścieżka na komputerze lokalnym.

5. Wybierz **przycisk OK,** aby zamknąć **okno** dialogowe Opcje.

## <a name="see-also"></a>Zobacz też

- [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Korzystanie z punktów przerwania](../debugger/using-breakpoints.md)