---
title: Samouczek Python w programie Visual Studio — krok 4, debugowanie
titleSuffix: ''
description: Krok 4 podstawowego przewodnika dotyczącego możliwości języka Python w programie Visual Studio, w którym opisano sposób uruchamiania kodu w języku Python w debugerze.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d7fe5a8b2275248c0fc68f9237e9e259973c567b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801727"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4. uruchamianie kodu w debugerze

**Poprzedni krok: [Użyj interaktywnego okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Poza zarządzaniem projektami, zapewnianie bogatego środowiska edycji i **interaktywnego** okna, program Visual Studio udostępnia w pełni funkcjonalne debugowanie dla kodu języka Python. W debugerze można uruchomić kod krok po kroku, włącznie z każdą iteracją pętli. Program można również wstrzymać w przypadku spełnienia określonych warunków. W dowolnym momencie, gdy program jest wstrzymany w debugerze, można odczytać cały stan programu i zmienić wartość zmiennych. Takie działania są niezbędne do śledzenia błędów programu, a także zapewniają bardzo przydatne ułatwienia w dokładnie podobny sposób do przepływu programu.

1. Zastąp kod w pliku *PythonApplication1.py* następującym kodem. Ta odmiana kodu rozszerza się, `make_dot_string` Aby można było zapoznać się z jego dyskretnymi krokami w debugerze. Umieszcza również `for` pętlę w `main` funkcji i uruchamia ją jawnie przez wywołanie tej funkcji:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Sprawdź, czy kod działa prawidłowo, naciskając klawisz **F5** lub wybierając polecenie **Debuguj**  >  **Rozpocznij debugowanie** menu. To polecenie uruchamia kod w debugerze, ale ponieważ nie wykonano żadnych czynności w celu wstrzymania programu, gdy jest on uruchomiony, po prostu drukuje wzorzec Wave dla kilku iteracji. Naciśnij dowolny klawisz, aby zamknąć okno dane wyjściowe.

    > [!Tip]
    > Aby zamknąć okno dane wyjściowe automatycznie po zakończeniu działania programu, wybierz polecenie **Narzędzia**  >  menu**Opcje** , rozwiń węzeł **Python** , wybierz pozycję **debugowanie**, a następnie wyczyść opcję **czekaj na dane wejściowe, gdy proces kończy się normalnie**:
    >
    > ![Opcja debugowania języka Python, aby zamknąć okno dane wyjściowe na normalnym zakończeniu programu](media/vs-getting-started-python-22-debugging5.png)

1. Aby ustawić punkt przerwania w `for` instrukcji, kliknij jeden raz na szarym marginesie przez ten wiersz lub przez umieszczenie karetki w tym wierszu i użycie polecenia **Debuguj**  >  **Przełącz punkt przerwania** (**F9**). Czerwona kropka pojawia się na szarym marginesie, aby wskazać punkt przerwania (zgodnie z poniższą strzałką):

    ![Ustawianie punktu przerwania](media/vs-getting-started-python-18-debugging1.png)

1. Ponownie uruchom debuger (**F5**) i zobacz, że uruchamianie kodu zostaje zatrzymane w wierszu z tym punktem przerwania. Tutaj można sprawdzić stos wywołań i zbadać zmienne. Zmienne, które są w zakresie, są wyświetlane w oknie **Autostarty** , gdy są zdefiniowane; Możesz również przełączyć się na widok **ustawień lokalnych** w dolnej części tego okna, aby pokazać wszystkie zmienne, które program Visual Studio znajdzie w bieżącym zakresie (łącznie z funkcjami), nawet zanim są zdefiniowane:

    ![Środowisko interfejsu użytkownika punktu przerwania dla języka Python](media/vs-getting-started-python-19-debugging2b.png)

1. Obserwuj pasek narzędzi debugowania (przedstawiony poniżej) w górnej części okna programu Visual Studio. Ten pasek narzędzi zapewnia szybki dostęp do najbardziej typowych poleceń debugowania (które można również znaleźć w menu **debugowanie** ):

    ![Najważniejsze przyciski paska narzędzi do debugowania](media/vs-getting-started-python-20-debugging3.png)

    Przyciski od lewej do prawej w następujący sposób:
    - **Kontynuuj** (**F5**) uruchamia program aż do następnego punktu przerwania lub do zakończenia programu.
    - **Przerwij wszystko** (**Ctrl** + **Alt** + **Break**) wstrzymuje długotrwały program.
    - **Zatrzymaj debugowanie** (**SHIFT** + **F5**) zatrzymuje program w dowolnym miejscu i zamyka debuger.
    - **Ponowne uruchomienie** (**Ctrl** + **SHIFT** + **F5**) powoduje zatrzymanie programu w dowolnym miejscu i ponowne uruchomienie go od początku w debugerze.
    - **Pokaż następną instrukcję** (**Alt** + **NUM** **&#42;**) przełącza do następnego wiersza kodu do uruchomienia. Jest to najbardziej przydatne, gdy poruszasz się po kodzie podczas sesji debugowania i chcesz szybko wrócić do punktu, w którym debuger jest wstrzymany.
    - **Wkrocz do** (**F11**) uruchamia następny wiersz kodu, wprowadzając do funkcji nazwanych.
    - **Krok nad** (**F10**) uruchamia następny wiersz kodu bez wchodzenia do funkcji nazwanych.
    - **Wyjdź** (**SHIFT** + **F11**) uruchamia pozostałą część bieżącej funkcji i wstrzymuje się w wywoływanym kodzie.

1. Przechodzenie do `for` instrukcji przy użyciu **kroku nad**. *Krokowe* oznacza, że debuger uruchamia bieżący wiersz kodu, w tym wszystkie wywołania funkcji, a następnie natychmiast zatrzymuje się ponownie. Zwróć uwagę, jak zmienna `i` jest teraz zdefiniowana w oknach **zmiennych lokalnych** i okienek. **Autos**

1. Przekrocz następny wiersz kodu, który wywołuje `make_dot_string` i wstrzymuje. Tutaj **krok powyżej** oznacza, że debuger działa w całości `make_dot_string` i wstrzymuje się, gdy zwraca. Debuger nie zatrzymuje się w tej funkcji, chyba że tam istnieje osobny punkt przerwania.

1. Kontynuuj przechodzenie przez kod jeszcze kilka razy i obserwuj, jak wartości w oknie **zmiennych lokalnych** lub **Autokorekty** zmieniają się.

1. W oknie zmienne **lokalne** lub **Autos** autozmienne kliknij dwukrotnie w kolumnie **wartość** , `i` `s` Aby edytować wartość. Naciśnij klawisz **Enter** lub kliknij dowolny obszar poza tą wartością, aby zastosować zmiany.

1. Kontynuuj przechodzenie przez kod przy użyciu **kroku do**. **Wkrocz do** oznacza, że debuger przechodzi wewnątrz dowolnego wywołania funkcji, dla którego ma informacje o debugowaniu, np `make_dot_string` .. Po wewnątrz można `make_dot_string` przeanalizować swoje zmienne lokalne i krokowo.

1. Kontynuuj wykonywanie **kroków krok po kroku** i Zauważ, że gdy osiągniesz koniec `make_dot_string` , następnym krokiem powróci do `for` pętli z nową wartością zwracaną w `s` zmiennej. Po ponownym przekroczeniu `print` instrukcji należy zauważyć, że **krok do** `print` nie jest wprowadzany do tej funkcji. Dzieje się tak, ponieważ `print` nie jest on pisany w języku Python, ale raczej kod natywny wewnątrz środowiska uruchomieniowego języka Python.

1. Kontynuuj korzystanie z **kroku** do momentu ponownego partway się w programie `make_dot_string` . Następnie użyj instrukcji **krok po kroku** , aby powrócić do `for` pętli. Po zakończeniu **kroku**debuger uruchamia resztę funkcji, a następnie automatycznie wstrzymuje się w kodzie wywołującym. Jest to bardzo przydatne w przypadku przechodzenia przez część długiej funkcji, która ma być debugowana, ale nie trzeba przechodzić przez resztę i nie chce ustawiać jawnego punktu przerwania w kodzie wywołującym.

1. Aby kontynuować uruchamianie programu do momentu osiągnięcia następnego punktu przerwania, użyj przycisku **Kontynuuj** (**F5**). Ponieważ masz punkt przerwania w `for` pętli, możesz przerwać kolejną iterację.

1. Przechodzenie przez setki iteracji pętli może być żmudnym, dzięki czemu program Visual Studio umożliwia dodanie *warunku* do punktu przerwania. Następnie debuger wstrzymuje program w punkcie przerwania tylko wtedy, gdy warunek jest spełniony. Na przykład można użyć warunku z punktem przerwania w instrukcji, `for` Aby wstrzymywać się tylko wtedy, gdy wartość `i` przekracza 1600. Aby ustawić ten warunek, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania i wybierz pozycję **warunki** (**Alt** + **F9**  >  **C**). W wyświetlonym oknie podręcznym **Ustawienia punktu przerwania** wprowadź `i > 1600` jako wyrażenie, a następnie wybierz przycisk **Zamknij**. Naciśnij klawisz **F5** , aby kontynuować i obserwować, że program uruchamia wiele iteracji przed następnym podziałem.

    ![Ustawianie warunku punktu przerwania](media/vs-getting-started-python-21-debugging4.png)

1. Aby uruchomić program do ukończenia, wyłącz punkt przerwania, klikając prawym przyciskiem myszy kropkę w marginesie i wybierając pozycję **Wyłącz punkt przerwania** (**Ctrl** + **F9**). Następnie wybierz pozycję **Kontynuuj** (lub naciśnij klawisz **F5**), aby uruchomić program. Po zakończeniu działania programu Program Visual Studio zatrzymuje swoją sesję debugowania i powraca do trybu edycji. Należy zauważyć, że punkt przerwania można również usunąć, zaznaczając jego kropkę lub klikając kropkę prawym przyciskiem myszy i wybierając polecenie **Usuń punkt przerwania**, ale również usuwa wszystkie ustawione warunki.

> [!Tip]
> W niektórych sytuacjach, takich jak błąd uruchamiania interpretera języka Python, okno danych wyjściowych może być wyświetlane tylko krótko, a następnie zamykane automatycznie bez podawania żadnych komunikatów o błędach. Jeśli tak się stanie, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, wybierz kartę **debugowanie** , a następnie Dodaj `-i` do pola **argumenty interpretera** . Ten argument powoduje, że interpreter przechodzi w tryb interaktywny po zakończeniu działania programu, dzięki czemu okno zostanie otwarte do momentu wprowadzenia **klawisza Ctrl** + **z**  >  **Enter** , aby wyjść.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Instalowanie pakietów w środowisku języka Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Debugowanie](debugging-python-in-visual-studio.md)
- [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md) zawiera pełną dokumentację funkcji debugowania programu Visual Studio.
