---
title: Python w programie Visual Studio samouczek krok 4, debugowanie
titleSuffix: ''
description: Krok 4 podstawowego przewodnika możliwości języka Python w programie Visual Studio, obejmujące sposób uruchamiania kodu języka Python w debugerze.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f6464986cb94ffa3ab3cc9264ab818112046ea9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "63002794"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4: Uruchom kod w debugerze

**Poprzedni krok: [Użyj interaktywnego okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Oprócz zarządzania projektami, zapewniając bogate środowisko edycji i **interaktywne** okno, Visual Studio zapewnia w pełni funkcjonalne debugowanie dla kodu języka Python. W debugerze można uruchomić kod krok po kroku, w tym każdej iteracji pętli. Można również wstrzymać program, gdy spełnione są określone warunki. W dowolnym momencie, gdy program jest wstrzymany w debugerze, można sprawdzić cały stan programu i zmienić wartość zmiennych. Takie działania są niezbędne do śledzenia błędów programu, a także zapewniają bardzo pomocne pomoce do dokładnego śledzenia dokładnego przepływu programu.

1. Zastąp kod w pliku *PythonApplication1.py* następującym. Ta odmiana kodu `make_dot_string` rozszerza się, dzięki czemu można zbadać jego dyskretne kroki w debugerze. Umieszcza również `for` pętlę `main` w funkcji i uruchamia ją jawnie, wywołując tę funkcję:

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

1. Sprawdź, czy kod działa poprawnie, naciskając **klawisz F5** lub wybierając polecenie menu **debugowania debugowania Debugowania.** > **Start Debugging** To polecenie uruchamia kod w debugerze, ale ponieważ nie zrobiono nic, aby wstrzymać program, gdy jest uruchomiony, po prostu drukuje wzorzec fali dla kilku iteracji. Naciśnij dowolny klawisz, aby zamknąć okno wyjściowe.

    > [!Tip]
    > Aby automatycznie zamknąć okno wyjściowe po zakończeniu programu, wybierz polecenie Menu**Opcje** **narzędzi,** > rozwiń węzeł **Python,** wybierz **debugowanie**, a następnie wyczyść opcję **Poczekaj na wejście, gdy proces zakończy się normalnie:**
    >
    > ![Opcja debugowania języka Python, aby zamknąć okno wyjściowe przy normalnym wyjściu programu](media/vs-getting-started-python-22-debugging5.png)

1. Ustaw punkt przerwania `for` w instrukcji, klikając raz na szarym marginesie przez ten wiersz lub umieszczając cieszkę w tym wierszu i używając polecenia **Debug** > **Toggle Breakpoint** (**F9**). Na szarym marginesie pojawi się czerwona kropka wskazująca punkt przerwania (jak zaznaczono poniższą strzałką):

    ![Ustawianie punktu przerwania](media/vs-getting-started-python-18-debugging1.png)

1. Uruchom debuger ponownie (**F5**) i zobacz, że uruchamianie kodu zatrzymuje się w wierszu z tym punktem przerwania. W tym miejscu można sprawdzić stos wywołań i zbadać zmienne. Zmienne, które znajdują się w zakresie są wyświetlane w oknie **Autos,** gdy są one zdefiniowane; można również przełączyć się do widoku **Locals** w dolnej części tego okna, aby wyświetlić wszystkie zmienne, które visual studio znajdzie w bieżącym zakresie (w tym funkcje), nawet przed ich zdefiniowaniem:

    ![Środowisko interfejsu użytkownika punktu przerwania dla języka Python](media/vs-getting-started-python-19-debugging2b.png)

1. Obserwuj pasek narzędzi debugowania (pokazany poniżej) w górnej części okna programu Visual Studio. Ten pasek narzędzi zapewnia szybki dostęp do najczęściejszych poleceń debugowania (które można również znaleźć w menu **debugowania):**

    ![Podstawowe przyciski paska narzędzi debugowania](media/vs-getting-started-python-20-debugging3.png)

    Przyciski od lewej do prawej w następujący sposób:
    - **Kontynuuj** **(F5)** uruchamia program do następnego punktu przerwania lub do zakończenia programu.
    - **Przerwa na wszystko** **(Ctrl**+**Alt**+**Break)** wstrzymuje długotrwały program.
    - **Zatrzymaj debugowanie** **(Shift**+**F5)** zatrzymuje program, gdziekolwiek jest, i kończy debuger.
    - **Uruchom ponownie** **(Ctrl**+**Shift**+**F5)** zatrzymuje program wszędzie tam, gdzie jest, i uruchamia go ponownie od początku w debugerze.
    - **Pokaż następną instrukcję** **(Alt**+**Num** **&#42;**) przełącza się do następnego wiersza kodu do uruchomienia. Jest to najbardziej przydatne podczas poruszania się po kodzie podczas sesji debugowania i chcesz szybko powrócić do punktu, w którym debuger jest wstrzymany.
    - **Step Into** (**F11**) uruchamia następny wiersz kodu, wprowadzając wywoływane funkcje.
    - **Step Over** **(F10)** uruchamia następny wiersz kodu bez wprowadzania wywoływanych funkcji.
    - **Step Out** **(Shift**+**F11)** uruchamia pozostałą część bieżącej funkcji i wstrzymuje kod wywołujący.

1. Krok nad `for` instrukcją za pomocą **Step Over**. *Stepping* oznacza, że debuger uruchamia bieżący wiersz kodu, w tym wywołania funkcji, a następnie natychmiast wstrzymuje ponownie. Zwróć uwagę, `i` jak zmienna jest teraz zdefiniowana w oknach **Lokalne** i **Automatyczne.**

1. Krok nad następnym wierszu kodu, który wywołuje `make_dot_string` i wstrzymuje. **Krok tutaj** w szczególności oznacza, że debuger uruchamia całość `make_dot_string` i wstrzymuje po jego powrocie. Debuger nie zatrzymuje się wewnątrz tej funkcji, chyba że istnieje tam oddzielny punkt przerwania.

1. Kontynuuj przechodzenie przez kod kilka razy i obserwować, jak zmieniają się wartości w oknie **Lokalne** lub **Autos.**

1. W oknie **Zmienne lokalne** lub **Automatyczne** kliknij dwukrotnie kolumnę `i` `s` **Wartość** dla zmiennych lub zmiennych, aby edytować wartość. Naciśnij **klawisz Enter** lub kliknij poza tą wartością, aby zastosować wszelkie zmiany.

1. Kontynuuj przechodzenie przez kod za pomocą **step into**. **Krok do** oznacza, że debuger wchodzi wewnątrz dowolnego wywołania funkcji, `make_dot_string`dla którego ma informacje debugowania, takich jak . Po `make_dot_string` wejściu do środka można zbadać jego zmienne lokalne i krok po kroku jego kodu specjalnie.

1. Kontynuuj przechodzenie z **Step Into** i zauważ, `make_dot_string`że po osiągnięciu `for` końca , następny krok `s` powraca do pętli z nową wartością zwracaną w zmiennej. Jak krok ponownie `print` do instrukcji, należy `print` zauważyć, że step **into** on nie wchodzi w tę funkcję. Dzieje się `print` tak dlatego, że nie jest napisane w języku Python, ale jest raczej natywny kod wewnątrz środowiska wykonawczego języka Python.

1. Kontynuuj korzystanie **z Step Into,** aż `make_dot_string`ponownie wejdź do . Następnie użyj **Step Out** i zwróć `for` uwagę, że powrócisz do pętli. Z **Step Out**, debuger uruchamia pozostałą część funkcji, a następnie automatycznie wstrzymuje w kodzie wywołującym. Jest to bardzo przydatne, gdy już krok przez niektóre części funkcji długi, które chcesz debugować, ale nie trzeba krok po kroku przez resztę i nie chcesz ustawić jawny punkt przerwania w kodzie wywołującym.

1. Aby kontynuować uruchamianie programu do momentu osiągnięcia następnego punktu przerwania, użyj **przycisku Kontynuuj** (**F5**). Ponieważ masz punkt przerwania `for` w pętli, można przerwać na następnej iteracji.

1. Przechodzenie przez setki iteracji pętli może być uciążliwe, więc Visual Studio umożliwia dodanie *warunku* do punktu przerwania. Debuger następnie wstrzymuje program w punkcie przerwania tylko wtedy, gdy warunek jest spełniony. Na przykład można użyć warunku z `for` punktem przerwania na instrukcji, `i` tak aby wstrzymywał tylko wtedy, gdy wartość przekracza 1600. Aby ustawić ten warunek, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania i wybierz **pozycję Warunki** (**Alt**+**F9** > **C**). W wyświetlonym okienku Ustawienia punktu `i > 1600` **przerwania** wprowadź jako wyrażenie i wybierz pozycję **Zamknij**. Naciśnij **klawisz F5,** aby kontynuować i obserwować, że program uruchamia wiele iteracji przed następną przerwą.

    ![Ustawianie warunku punktu przerwania](media/vs-getting-started-python-21-debugging4.png)

1. Aby uruchomić program do zakończenia, wyłącz punkt przerwania, klikając prawym przyciskiem myszy i wybierając **pozycję Wyłącz punkt przerwania** (**Ctrl**+**F9**). Następnie wybierz **przycisk Kontynuuj** (lub naciśnij **klawisz F5),** aby uruchomić program. Po zakończeniu programu visual studio zatrzymuje jego sesji debugowania i powraca do trybu edycji. Należy zauważyć, że można również usunąć punkt przerwania, klikając jego kropkę, ale to również usuwa wszystkie ustawione warunki.

> [!Tip]
> W niektórych sytuacjach, takich jak niepowodzenie uruchamiania samego interpretera języka Python, okno danych wyjściowych może pojawić się tylko na krótko, a następnie zamknij automatycznie, nie dając szansy na wyświetlenie komunikatów o błędach. W takim przypadku kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań**, wybierz **polecenie Właściwości**, wybierz kartę **Debugowanie,** a następnie dodaj `-i` do pola Argumenty **interpretera.** Ten argument powoduje, że interpreter przejść do trybu interaktywnego po zakończeniu programu, dzięki tym samym utrzymanie okna otwarte, dopóki nie zostanie wprowadzony **Ctrl**+**Z** > **Enter,** aby zakończyć.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Instalowanie pakietów w środowisku Pythona](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Głębiej

- [Debugging](debugging-python-in-visual-studio.md)
- [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md) zawiera pełną dokumentację funkcji debugowania programu Visual Studio.
