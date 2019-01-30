---
title: Debugowania języka Python w programie Visual Studio — samouczek krok 4,
titleSuffix: ''
description: Krok 4 przewodnika podstawowe możliwości języka Python w programie Visual Studio, obejmujących sposobu uruchamiania kodu w języku Python w debugerze.
ms.date: 01/28/2019
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e48619c34774425986888a9210c2c533e4b5d0db
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231899"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4. Uruchamianie kodu w debugerze

**Poprzedniego kroku: [Korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Oprócz zarządzania projektami, zapewniając bogate środowisko, edytowania i **Interactive** okna, program Visual Studio oferuje w pełni funkcjonalne debugowania dla kodu w języku Python. W debugerze można uruchomić kod krok po kroku, łącznie z każdą iteracją pętli. Można również wstrzymać program zawsze wtedy, gdy są spełnione określone warunki. W dowolnym momencie gdy program jest wykorzystywana w debugerze, można sprawdzić stan całego programu i zmień wartości zmiennych. Takie działania są niezbędne do śledzenia szczegółów błędów programu i również zapewniają pomoc bardzo przydatne dla dokładnie zgodnie z przepływem programu dokładne.

1. Zastąp kod w *PythonApplication1.py* pliku następującym kodem. Taka zmiana kodu rozwija `make_dot_string` tak, aby zbadać jego dyskretnych kroków w debugerze. Ponadto umieszcza `for` pętli do `main` funkcji i uruchamia go jawnie, przez wywołanie tej funkcji:

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

1. Upewnij się, że kod działa poprawnie, naciskając klawisz **F5** lub wybierając **debugowania** > **Rozpocznij debugowanie** polecenia menu. To polecenie uruchamia kod w debugerze, ale ponieważ jeszcze nie wykonano żadnych czynności, aby zatrzymać program i jest uruchomiona, po prostu wyświetla wzorzec wave dla kilku iteracji. Naciśnij dowolny klawisz, aby zamknąć okno danych wyjściowych.

    > [!Tip]
    > Aby zamknąć okno danych wyjściowych automatycznie po zakończeniu program, należy zastąpić `main()` wywołania z następującym kodem:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Ustaw punkt przerwania na `for` instrukcji, klikając szary marginesie przez ten wiersz lub umieszczając karetkę w tym wierszu i przy użyciu **debugowania** > **Przełącz punkt przerwania** poleceń () **F9**). Czerwona kropka pojawi się szare marginesie, aby wskazać punkt przerwania (jak wspomniano, strzałką poniżej):

    ![Ustawienie punktu przerwania](media/vs-getting-started-python-18-debugging1.png)

1. Ponownie uruchom debuger (**F5**) i zobacz, zatrzymuje kod uruchomiony w wierszu zawierającym ten punkt przerwania. W tym miejscu możesz sprawdzić wywołanie stosu i Sprawdź zmienne. Zmienne, które są w zakresie są wyświetlane w **automatyczne** okna, jeśli są one definiowane; może również przełącznik **zmiennych lokalnych** widoku w dolnej części tego okna, aby pokazać wszystkie zmienne programu Visual Studio znajduje się w bieżący zakres (takie jak functions), nawet przed definiowania:

    ![Punkt przerwania możliwości interfejsu użytkownika dla języka Python](media/vs-getting-started-python-19-debugging2b.png)

1. Wzdłuż górnej części okna programu Visual Studio, należy przestrzegać pasku narzędzi debugowania (pokazana poniżej). Ten pasek narzędzi zapewnia szybki dostęp do najczęściej używanych poleceń debugowania (które również znajdują się na **debugowania** menu):

    ![Podstawowe przycisków na pasku narzędzi debugowania](media/vs-getting-started-python-20-debugging3.png)

    Przyciski od lewej do prawej w następujący sposób:
    - **Kontynuuj** (**F5**) uruchamia program do następnego punktu przerwania lub do chwili zakończenia programu.
    - **Przerwij wszystkie** (**Ctrl**+**Alt**+**Przerwij**) zatrzymuje program długoterminowych.
    - **Zatrzymaj debugowanie** (**Shift**+**F5**) zatrzymuje program, wszędzie tam, gdzie jest i kończy pracę debugera.
    - **Uruchom ponownie** (**Ctrl**+**Shift**+**F5**) zatrzymuje program, wszędzie tam, gdzie jest i uruchamia go ponownie od samego początku w debuger.
    - **Pokaż następną instrukcję** (**Alt**+**Num** **&#42;**) przełącza do następnego wiersza kodu do uruchomienia. Jest to najbardziej przydatne w przypadku, gdy nawigację w kodzie podczas sesji debugowania i chcesz szybko powrócić do punktu, w której debuger jest wstrzymana.
    - **Step Into** (**F11**) uruchamia następnego wiersza kodu, wprowadzanie do wywoływanej funkcji.
    - **Step Over** (**F10**) uruchamia następnego wiersza kodu, bez konieczności wprowadzania do wywoływanej funkcji.
    - **Step Out** (**Shift**+**F11**) jest uruchamiany w pozostałej części bieżącą funkcję i wstrzymuje w wywoływanym kodzie.

1. Przekrocz nad `for` przy użyciu instrukcji **Step Over**. *Przechodzenie krok po kroku* oznacza, że debuger jest uruchamiany bieżącego wiersza kodu, w tym wszelkie wywołania funkcji i natychmiast wstrzymuje ponownie. Zwróć uwagę jak zmienna `i` teraz jest zdefiniowany w **lokalne** i **Autos** systemu windows.

1. Przekrocz nad następnego wiersza kodu, który wywołuje `make_dot_string` i zatrzymuje się. **Step Over** tutaj specjalnie oznacza, że debuger działa na całym `make_dot_string` i zatrzymuje się, gdy zwraca ono. Debuger nie zatrzymuje wewnątrz tej funkcji, chyba że istnieje oddzielny punkt przerwania.

1. Kontynuuj przechodzenie krok po kroku przez kod jeszcze kilka razy i obserwuj jak wartości w **lokalne** lub **Autos** okna zmiany.

1. W **lokalne** lub **Autos** okna, kliknij dwukrotnie plik w **wartość** kolumny albo `i` lub `s` zmienne, aby edytować wartość. Naciśnij klawisz **Enter** lub kliknij poza tę wartość, aby zastosować zmiany.

1. Kontynuuj krokowego wykonywania kodu za pomocą **Step Into**. **Step Into** oznacza, że debuger przejdzie wewnątrz każde wywołanie funkcji, dla której ma on, debugowanie informacji, takich jak `make_dot_string`. Jeden raz w obrębie `make_dot_string` możesz sprawdzić jego zmienne lokalne i przejrzeć jego kod specjalnie.

1. Kontynuuj przechodzenie krok po kroku z **Step Into** i zwróć uwagę, że w przypadku osiągnięcia końca `make_dot_string`, następnym krokiem powraca do `for` pętli za pomocą nowych wartości zwracanej w `s` zmiennej. Podczas wykonywania kroków ponownie do `print` instrukcji, zwróć uwagę, że **Step Into** na `print` nie wejdzie w tej funkcji. Jest to spowodowane `print` nie jest napisany w języku Python, ale raczej natywny kod wewnątrz środowiska uruchomieniowego języka Python.

1. Nadal korzystać z **Step Into** dopóki nie jesteś ponownie zatrzymuje do `make_dot_string`. Następnie użyj **Step Out** i zwróć uwagę, że można wrócić do `for` pętli. Za pomocą **Step Out**, Debuger jest uruchamiany w pozostałej części funkcji i automatycznie wstrzymuje w wywoływanym kodzie. Jest to bardzo przydatne, gdy już schodkowego za pośrednictwem niektórych części długich funkcji, który chcesz debugować, ale nie muszą przejść przez pozostałe i dla których nie chcesz ustawić jawne punkt przerwania w kodzie.

1. Aby kontynuować, program działa aż do osiągnięcia następnego punktu przerwania, użyj **Kontynuuj** (**F5**). Ponieważ ma punkt przerwania w `for` pętli, Przerwij przy następnej iteracji.

1. Krokowe wykonywanie setki iteracji pętli może być uciążliwe, więc program Visual Studio pozwala dodać *warunek* do punktu przerwania. Debuger następnie wstrzymuje program w punkcie przerwania, tylko wtedy, gdy warunek jest spełniony. Na przykład można użyć warunku z punktu przerwania na `for` instrukcji, tak że wstrzymuje tylko gdy wartość `i` przekracza 1600. Aby ustawić ten warunek, kliknij prawym przyciskiem myszy czerwony punktu przerwania kropki (.), a następnie wybierz **warunki** (**Alt**+**F9** > **C**). W **ustawienia punktu przerwania** okna podręcznego, który pojawia się, wprowadź `i > 1600` jako wyrażenie, a następnie wybierz pozycję **Zamknij**. Naciśnij klawisz **F5** aby kontynuować, a następnie sprawdź, czy program ma być uruchamiany wiele iteracji przed następnym podziału.

    ![Ustawienie warunek punktu przerwania](media/vs-getting-started-python-21-debugging4.png)

1. Aby uruchomić program do zakończenia, wyłączenie punktu przerwania, klikając prawym przyciskiem myszy i wybierając polecenie **Wyłącz punkt przerwania** (**Ctrl**+**F9**). Następnie wybierz pozycję **Kontynuuj** (lub naciśnij **F5**) do uruchomienia programu. Po zakończeniu program Visual Studio zatrzymuje sesję debugowania i zwraca do trybu edycji. Należy pamiętać, że możesz także usunąć punkt przerwania, klikając jej kropką, ale spowoduje to również usunięcie wszelkich warunek, który został ustawiony.

> [!Tip]
> W niektórych sytuacjach, takich jak błąd, aby uruchomić interpretera języka Python, w oknie danych wyjściowych może są wyświetlane tylko chwilę, a następnie Zamknij automatycznie, nie dając Ci się zobaczyć komunikaty błędów. Jeśli tak się stanie, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz opcję **właściwości**, wybierz opcję **debugowania** kartę, a następnie dodaj `-i` do  **Argumenty interpreter** pola. Ten argument powoduje, że interpreter przejść do trybu interaktywnego, po zakończeniu działania programu, a tym samym utrzymywanie okna otwarte do momentu wprowadzenia **Ctrl**+**Z**  >  **Enter** aby wyjść.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Instalowanie pakietów w środowisku Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Debugowanie](debugging-python-in-visual-studio.md)
- [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md) zapewnia pełną dokumentację programu Visual Studio w funkcji debugowania.
