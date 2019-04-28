---
title: Wyświetl wątki w debugerze | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fddd8efd11d2a3d61f0cff33cb832ebd8a0c5d2a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406940"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Wyświetl wątki w debugerze programu Visual Studio za pomocą okna wątki (C#, Visual Basic, C++)
W **wątków** okna, możesz sprawdzić i Praca z wątkami w aplikacji, który debugujesz. Aby uzyskać szczegółowe instrukcje dotyczące sposobu używania **wątków** okna, zobacz [instruktażu: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Korzystanie z okna wątków
 **Wątków** okno zawiera tabelę, w którym każdy wiersz w tym artykule opisano oddzielnego wątku w aplikacji. Domyślnie w tabeli wymieniono wszystkie wątki w swojej aplikacji, ale można filtrować listę, aby wyświetlić wątki, które Cię interesują. Każda kolumna zawiera opis innego typu informacji. Można także ukryć niektóre kolumny. Jeśli wyświetlane są wszystkie kolumny, następujące kolumny są wyświetlane, od lewej do prawej:

- **Flaga**: W tej kolumnie bez etykiety można oznaczyć wątek, do którego chcesz zwrócić szczególną uwagę. Aby uzyskać informacje o sposobie Flagowanie wątku, zobacz [jak: Oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md).

- **Bieżący wątek**: W tej kolumnie bez etykiety żółta strzałka wskazuje bieżący wątek. Konspekt Strzałka wskazuje bieżący kontekst debugera dla wątku innej niż bieżąca.

- **ID**: Wyświetla numer identyfikacyjny dla każdego wątku.

- **Zarządzany identyfikator**: Wyświetla numery identyfikacyjne zarządzanych dla wątków zarządzanych.

- **Kategoria**: Wyświetla kategorii wątki wątki interfejsu użytkownika, obsługa wywołania procedury zdalnej lub wątków roboczych. Kategoria specjalne identyfikuje wątku głównego aplikacji.

- **Nazwa**: Identyfikuje każdy wątek przy użyciu nazwy, jeśli taki istnieje, lub jako \<Brak nazwy >.

- **Lokalizacja**: Pokazuje, gdzie wątek jest uruchomiony. Można rozwinąć tej lokalizacji, aby wyświetlić pełny stos wywołania dla wątku.

- **Priorytet**: Zaawansowane (domyślnie ukryte) wyświetlana kolumna priorytet lub pierwszeństwo przypisana przez system do każdego wątku.

- **Maska koligacji**: Zaawansowane kolumnę (domyślnie ukryte) przedstawiającą Maska koligacji procesorów dla każdego wątku. W systemie wieloprocesorowym Maska koligacji Określa, które procesory, na których można uruchomić wątku.

- **Zawieszone liczba**: Zaawansowane (domyślnie ukryte) wyświetlana kolumna licznik wstrzymany. Liczba ta określa, czy można uruchomić wątku. Aby uzyskać więcej informacji na temat liczby wstrzymania zobacz [Zablokuj i Odblokuj wątki](#freeze-and-thaw-threads).

- **Nazwa procesu**: Zaawansowane kolumny (domyślnie ukryte), który wyświetla ten proces, do której należy każdego wątku. Dane w tej kolumnie może być przydatne podczas debugowania wielu procesów.

- **Identyfikator procesu**: Zaawansowane kolumny (domyślnie ukryte), który wyświetla identyfikator procesu, do której należy każdego wątku.

- **Kwalifikator transportu**: Zaawansowane kolumny (domyślnie ukryte) który jednoznacznie identyfikuje maszyny, do którego jest podłączony debugera.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Aby wyświetlić okno wątków w trybie przerwania lub w trybie uruchamiania

- Visual Studio jest w trybie debugowania, wybierz **debugowania** menu wskaż **Windows**, a następnie wybierz pozycję **wątków**.

### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumny

- Na pasku narzędzi u góry **wątków** wybierz **kolumn**. Następnie zaznacz lub wyczyść nazwę kolumny, który chcesz wyświetlić lub ukryć.

## <a name="display-flagged-threads"></a>Wyświetlanie oflagowane wątki
 Można flagę wątku, który chcesz poświęcić szczególną uwagę, oznaczając je za pomocą ikony w **wątków** okna. Aby uzyskać więcej informacji, zobacz [jak: Oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md). W **wątków** oknie, użytkownik może wyświetlić wszystkie wątki lub tylko oflagowane wątki.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki

- Wybierz **Pokaż wątki tylko oflagowane** na pasku narzędzi u góry **wątków** okna. (Jeśli go jest nieaktywne, musisz najpierw oflagowania wątków.)

## <a name="freeze-and-thaw-threads"></a>Zablokuj i Odblokuj wątki
 Zablokowanie wątku systemu nie uruchamia wykonywanie wątku, nawet jeśli zasoby są dostępne.

 W kodzie natywnym można wstrzymać lub wznowić wątków przez wywołanie funkcji Windows `SuspendThread` i `ResumeThread`. Lub wywoływać funkcje MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) i [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Jeśli wywołasz `SuspendThread` lub `ResumeThread`, *zawieszone liczba* objętego **wątków** okno zostanie zmieniona. Liczba wstrzymanych nie powoduje zmiany blokowanie lub odblokowywanie wątków natywnych. Wątek nie można wykonać w kodzie natywnym, chyba że jest rozmrożone i został wstrzymany liczbę zero.

 W kodzie zarządzanym licznik wstrzymany ulega zmianie po użytkownik blokowanie lub odblokowywanie wątków. Jeśli w kodzie zarządzanym można zablokować wątek, jego licznik wstrzymany to 1. Po zablokowaniu wątków w kodzie macierzystym jego licznik wstrzymany ma wartość 0, o ile nie użyto `SuspendThread` wywołania.

> [!NOTE]
> Podczas debugowania wywołań z kodu natywnego do zarządzanego kodu, kod zarządzany działa w tym samym wątku fizycznym jako kodu natywnego, która nazwała go. Zawieszanie lub zawiesza się Wątek macierzysty również zawiesza się kod zarządzany.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Na blokowanie lub odblokowywanie wykonanie wątku

- Na pasku narzędzi u góry **wątków** wybierz **Zablokuj wątki** lub **Odblokuj wątki**.

     Ta akcja dotyczy tylko wątki, które są wybrane w **wątków** okna.

### <a name="switch-to-another-thread"></a>Przełączanie na inny wątek

Żółta strzałka wskazuje bieżący wątek (i lokalizacja wskaźnik wykonania). Zielona strzałka z zakręconym ogonkiem wskazuje, że innym niż bieżący wątek jest bieżący kontekst debugera.

#### <a name="to-switch-to-another-thread"></a>Aby przełączyć się do innego wątku

- Wykonaj jedną z następujących czynności:

    - Kliknij dwukrotnie wątek.

    - Kliknij prawym przyciskiem myszy wątku, a następnie wybierz pozycję **Przełącz do wątku**.

## <a name="group-and-sort-threads"></a>Grupowanie i sortowanie wątków
 Grupowanie wątków nagłówek pojawia się w tabeli dla każdej grupy. Nagłówek zawiera opis grupy, takie jak **wątku roboczego** lub **wątki bez flagi**, a kontrolka drzewa. Wątki elementu członkowskiego każdej grupy pojawiają się pod nagłówkiem grupy. Jeśli chcesz ukryć wątków członka grupy, formant drzewa Aby zwinąć grupy.

 Grupowanie ma pierwszeństwo przed sortowania, można Grupuj wątki według kategorii, na przykład i sortować je według Identyfikatora w ramach każdej kategorii.

### <a name="to-sort-threads"></a>Aby posortować wątków

1. Na pasku narzędzi u góry **wątków** okna, wybierz przycisk u góry dowolnej kolumny.

     Wątki, teraz są sortowane według wartości w tej kolumnie.

2. Jeśli chcesz odwrócić porządek sortowania, wybierz ten sam przycisk ponownie.

     Wątki, które znajdowały się u góry listy teraz pojawiają się na dole.

### <a name="to-group-threads"></a>Grupa wątków

- W **wątków** pasek narzędzi okna, wybierz opcję **Grupuj według** , a następnie wybierz kryteria, których chcesz grupowanie wątków przez.

### <a name="to-sort-threads-within-groups"></a>Aby posortować wątków w grupach

1. Na pasku narzędzi u góry **wątków** wybierz **Grupuj według** , a następnie wybierz kryteria, których chcesz grupowanie wątków przez.

2. W **wątków** okna, wybierz przycisk u góry dowolnej kolumny.

     Wątki, teraz są sortowane według wartości w tej kolumnie.

### <a name="to-expand-or-collapse-all-groups"></a>Rozwiń lub Zwiń wszystkie grupy

- Na pasku narzędzi u góry **wątków** wybierz **Rozwiń grupy** lub **Zwiń grupy**.

## <a name="search-for-specific-threads"></a>Wyszukaj określone wątki
 Możesz wyszukać wątki, które odpowiadają określony ciąg w **wątków** okna. Podczas wyszukiwania dla wątków, w oknie zostaną wyświetlone wszystkie wątki dopasowywania ciągu wyszukiwania w dowolnej kolumnie. Informacje te obejmują lokalizacji wątku, który pojawia się w górnej części stosu wywołań w **lokalizacji** kolumny. Domyślnie przeszukiwane nie jest pełny stos wywołania.

### <a name="to-search-for-specific-threads"></a>Aby wyszukać określone wątki

1. Na pasku narzędzi u góry **wątków** okna, przejdź do **wyszukiwania** pole, a następnie:

     - Wprowadź wyszukiwany ciąg, a następnie naciśnij klawisz **Enter**.

     \- lub —

     - Wybierz z listy rozwijanej obok pozycji **wyszukiwania** polu, a następnie wybierz wyszukiwany ciąg z poprzedniego wyszukiwania.

2. (Opcjonalnie) Aby dołączyć pełny stos wywołań wyszukiwania, wybierz **stos wywołań wyszukiwania**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Wyświetlić stosy wywołań wątku i przełączać się między ramki
W programie wielowątkowym każdy wątek ma swój własny stos wywołań. **Wątków** okna zapewnia wygodny sposób, aby wyświetlić te stosów.

> [!TIP]
> Wizualna reprezentacja stos wywołań dla każdego wątku, można użyć [stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md) okna.

### <a name="to-view-the-call-stack-of-a-thread"></a>Aby wyświetlić stos wywołań wątku

- W **lokalizacji** kolumny, zaznacz odwróconą trójkąta obok lokalizacji wątku.

     Lokalizacja rozwija Pokaż stos wywołań dla wątku.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Aby wyświetlić lub Zwiń stosy wywołań wszystkich wątków

- Na pasku narzędzi u góry **wątków** wybierz **rozwiń stosy wywołań** lub **Zwiń stosy wywołań**.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)