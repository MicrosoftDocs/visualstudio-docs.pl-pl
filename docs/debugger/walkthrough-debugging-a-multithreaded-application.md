---
title: Wyświetlanie wątków w debugerze | Microsoft Docs
description: Użyj wątków do badania i kontrolowania wątków. Można grupować, sortować, flagować, zamrażać, odrozmrażać i wyszukiwać wątki, wybierać kolumny i wyświetlać stosy wywołań.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b02d980292eaed40c7c1598c772b52f695bf23e2
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149706"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Wyświetlanie wątków w debugerze programu Visual Studio przy użyciu okna wątków (C#, Visual Basic, C++)
W oknie **wątki** można analizować i współpracować z wątkami w debugowanej aplikacji. Aby uzyskać wskazówki krok po kroku dotyczące korzystania z okna **wątków** , zobacz [Przewodnik: debugowanie przy użyciu okna wątki](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Korzystanie z okna wątków
 Okno **wątki** zawiera tabelę, w której każdy wiersz zawiera opis oddzielnego wątku w aplikacji. Domyślnie w tabeli znajduje się lista wszystkich wątków w aplikacji, ale można filtrować listę, aby pokazać tylko te wątki, które Cię interesują. Każda kolumna zawiera informacje o różnych typach. Możesz również ukryć niektóre kolumny. Jeśli zostaną wyświetlone wszystkie kolumny, wyświetlane są następujące kolumny od lewej do prawej:

- **Flaga**: w tej kolumnie bez etykiet można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę. Aby uzyskać informacje o sposobie oflagowania wątku, zobacz [How to: flag i unflaging](../debugger/how-to-flag-and-unflag-threads.md)Threads.

- **Bieżący wątek**: w tej kolumnie bez etykiety, żółta strzałka wskazuje bieżący wątek. Konspekt strzałki wskazuje bieżący kontekst debugera dla wątku niebieżącego.

- **Identyfikator**: Wyświetla numer identyfikacyjny dla każdego wątku.

- **Identyfikator zarządzany**: wyświetla zarządzane numery identyfikacyjne dla zarządzanych wątków.

- **Kategoria**: wyświetla kategorię wątków jako wątki interfejsu użytkownika, procedury obsługi zdalnego wywoływania procedur lub wątki robocze. Specjalna kategoria identyfikuje główny wątek aplikacji.

- **Nazwa**: identyfikuje każdy wątek według nazwy, jeśli ma jeden, lub jako \<No Name> .

- **Lokalizacja**: pokazuje, gdzie działa wątek. Można rozwinąć tę lokalizację, aby pokazać pełny stos wywołań wątku.

- **Priorytet**: kolumna zaawansowana (domyślnie ukryta), która wyświetla priorytet lub pierwszeństwo przypisany system do każdego wątku.

- **Maska koligacji**: kolumna zaawansowana (domyślnie ukryta), która pokazuje maskę koligacji procesora dla każdego wątku. W systemie wieloprocesorowym maska koligacji określa procesory, w których można uruchomić wątek.

- **Liczba wstrzymanych**: kolumna zaawansowana (domyślnie ukryta), która wyświetla liczbę wstrzymanych. Ta liczba określa, czy można uruchomić wątek. Aby uzyskać więcej informacji o wstrzymanych licznikach, zobacz [blokowanie i odblokowywanie wątków](#freeze-and-thaw-threads).

- **Nazwa procesu**: kolumna zaawansowana (domyślnie ukryta), która wyświetla proces, do którego należy każdy wątek. Dane w tej kolumnie mogą być przydatne podczas debugowania wielu procesów.

- **Identyfikator procesu**: kolumna zaawansowana (domyślnie ukryta), która wyświetla identyfikator procesu, do którego należy każdy wątek.

- **Kwalifikator transportu**: Zaawansowana kolumna (domyślnie ukryta), która jednoznacznie identyfikuje maszynę, do której jest podłączony debuger.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Aby wyświetlić okno wątki w trybie przerwania lub w trybie uruchamiania

- Gdy program Visual Studio jest w trybie debugowania, wybierz menu **Debuguj** , wskaż pozycję **Windows**, a następnie wybierz pozycję **wątki**.

### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumnę

- Na pasku narzędzi u góry okna **wątki** wybierz pozycję **kolumny**. Następnie wybierz lub wyczyść nazwę kolumny, która ma być wyświetlana lub ukryta.

## <a name="display-flagged-threads"></a>Wyświetl oflagowane wątki
 Można oflagować wątek, który ma dawać szczególną uwagę, poprzez oznaczenie go ikoną w oknie **wątki** . Aby uzyskać więcej informacji, zobacz [How to: flag i unflaging Threads](../debugger/how-to-flag-and-unflag-threads.md). W oknie **wątki** można wyświetlić wszystkie wątki lub tylko Oflagowane wątki.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki

- Wybierz pozycję **Pokaż wątki oflagowane tylko** na pasku narzędzi u góry okna **wątki** . (Jeśli jest wygaszony, należy najpierw oflagować niektóre wątki).

## <a name="freeze-and-thaw-threads"></a>Zamrażanie i odblokowywanie wątków
 W przypadku zablokowania wątku system nie rozpoczyna wykonywania wątku, nawet jeśli dostępne są zasoby.

 W kodzie natywnym można wstrzymywać lub wznawiać wątki przez wywoływanie funkcji systemu Windows `SuspendThread` i `ResumeThread` . Lub wywołaj funkcje MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) i [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). W przypadku wywołania `SuspendThread` lub zostanie `ResumeThread` zmieniona *Liczba wstrzymań* wyświetlana w oknie **wątki** . Liczba wstrzymanych nie zmienia się w przypadku zablokowania lub odblokowania wątku natywnego. Wątek nie może zostać wykonany w kodzie natywnym, chyba że jest odmrożony i ma wstrzymaną liczbę zero.

 W kodzie zarządzanym Liczba wstrzymanych zmian w przypadku zablokowania lub odblokowania wątku. W przypadku zablokowania wątku w kodzie zarządzanym jego liczba wstrzymań wynosi 1. W przypadku zablokowania wątku w kodzie natywnym jego wstrzymana liczba jest równa 0, chyba że użyto `SuspendThread` wywołania.

> [!NOTE]
> Podczas debugowania wywołania z kodu natywnego do kodu zarządzanego, kod zarządzany jest uruchamiany w tym samym wątku fizycznym co kod natywny, który go wywołał. Zawieszanie lub zamrażanie wątku natywnego blokuje również kod zarządzany.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Aby zablokować lub odblokować wykonywanie wątku

- Na pasku narzędzi u góry okna **wątki** wybierz opcję **Zablokuj wątki** lub **rozmrażaj wątki**.

     Ta akcja ma wpływ tylko na wątki, które są wybrane w oknie **wątki** .

### <a name="switch-to-another-thread"></a>Przełącz do innego wątku

Żółta strzałka wskazuje bieżący wątek (i lokalizację wskaźnika wykonywania). Zielona strzałka z ogonem klamrowym wskazuje, że wątek inny niż bieżący ma bieżący kontekst debugera.

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku

- Wykonaj jedną z następujących czynności:

  - Kliknij dwukrotnie dowolny wątek.

  - Kliknij prawym przyciskiem myszy wątek i wybierz polecenie **Przełącz do wątku**.

## <a name="group-and-sort-threads"></a>Grupuj i Sortuj wątki
 Gdy grupujesz wątki, w tabeli dla każdej grupy pojawi się nagłówek. Nagłówek zawiera opis grupy, taki jak **wątek roboczy** lub **wątki nieoflagowane** oraz formant drzewa. Wątki elementów członkowskich każdej grupy są wyświetlane pod nagłówkiem grupy. Aby ukryć wątki elementów członkowskich dla grupy, należy zwinąć grupę przy użyciu kontrolki drzewa.

 Ponieważ grupowanie ma pierwszeństwo przed sortowaniem, można grupować wątki według kategorii, na przykład, a następnie sortować je według identyfikatora w każdej kategorii.

### <a name="to-sort-threads"></a>Aby posortować wątki

1. Na pasku narzędzi u góry okna **wątki** wybierz przycisk w górnej części dowolnej kolumny.

     Wątki są teraz sortowane według wartości w tej kolumnie.

2. Jeśli chcesz odwrócić porządek sortowania, zaznacz ten sam przycisk ponownie.

     Wątki, które pojawiły się w górnej części listy, teraz pojawiają się u dołu.

### <a name="to-group-threads"></a>Do grup wątków

- Na pasku narzędzi okna **wątki** wybierz listę **Grupuj według** , a następnie wybierz kryteria, według których chcesz grupować wątki.

### <a name="to-sort-threads-within-groups"></a>Aby posortować wątki w grupach

1. Na pasku narzędzi u góry okna **wątki** wybierz listę **Grupuj według** , a następnie wybierz kryteria, według których chcesz grupować wątki.

2. W oknie **wątki** wybierz przycisk w górnej części dowolnej kolumny.

     Wątki są teraz sortowane według wartości w tej kolumnie.

### <a name="to-expand-or-collapse-all-groups"></a>Aby rozwinąć lub zwinąć wszystkie grupy

- Na pasku narzędzi u góry okna **wątki** wybierz **Rozwiń grupy** lub **Zwiń grupy**.

## <a name="search-for-specific-threads"></a>Wyszukaj określone wątki
 W oknie **wątki** można wyszukać wątki pasujące do określonego ciągu. Podczas wyszukiwania wątków w oknie są wyświetlane wszystkie wątki pasujące do ciągu wyszukiwania w dowolnej kolumnie. Te informacje obejmują lokalizację wątku wyświetlaną w górnej części stosu wywołań w kolumnie **Lokalizacja** . Domyślnie cały stos wywołań nie jest przeszukiwany.

### <a name="to-search-for-specific-threads"></a>Aby wyszukać określone wątki

1. Na pasku narzędzi u góry okna **wątki** przejdź do pola **wyszukiwania** , a następnie:

     - Wprowadź ciąg wyszukiwania, a następnie naciśnij klawisz **Enter**.

     \- oraz

     - Wybierz listę rozwijaną obok pola **wyszukiwania** i wybierz ciąg wyszukiwania z poprzedniego wyszukiwania.

2. Obowiązkowe Aby dołączyć pełny stos wywołań w wyszukiwaniu, wybierz pozycję **Wyszukaj stos wywołań**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Wyświetlaj stosy wywołań wątku i przełączaj między ramkami
W programie wielowątkowym każdy wątek ma własny stos wywołań. Okno **wątki** zapewnia wygodny sposób wyświetlania tych stosów.

> [!TIP]
> Aby uzyskać wizualną reprezentację stosu wywołań dla każdego wątku, użyj okna [stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md) .

### <a name="to-view-the-call-stack-of-a-thread"></a>Aby wyświetlić stos wywołań wątku

- W kolumnie **Lokalizacja** zaznacz odwrócony trójkąt obok lokalizacji wątku.

     Lokalizacja rozszerza się, aby pokazać stos wywołań wątku.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Aby wyświetlić lub zwinąć stosy wywołań wszystkich wątków

- Na pasku narzędzi u góry okna **wątki** wybierz opcję **Rozwiń stosy wywołań** lub **Zwiń stosy wywołań**.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)
