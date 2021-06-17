---
title: Python w Visual Studio samouczku, krok 4, debugowanie
titleSuffix: ''
description: Krok 4 podstawowego przewodnika po możliwościach języka Python w języku Visual Studio, który obejmuje sposób uruchamiania kodu języka Python w debugerze.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13080f69de9a8bfc6b1da35a7126f1f0c89a64c7
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254865"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4. Uruchamianie kodu w debugerze

**Poprzedni krok: [Korzystanie z okna Interactive REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Oprócz zarządzania projektami, zapewniania rozbudowanych  możliwości edytowania i okna interaktywnego, Visual Studio zapewnia w pełni funkcjonalne debugowanie kodu w języku Python. W debugerze można uruchamiać kod krok po kroku, w tym każdą iterację pętli. Możesz również wstrzymać program za każdym razem, gdy zostaną spełnione określone warunki. W dowolnym momencie, gdy program jest wstrzymany w debugerze, można zbadać cały stan programu i zmienić wartość zmiennych. Takie akcje są niezbędne do śledzenia błędów programu, a także zapewniają bardzo przydatne pomoc dla dokładnego śledzenia przepływu programu.

1. Zastąp kod w pliku *PythonApplication1.py* poniższym kodem. Ta odmiana kodu rozszerza `make_dot_string` się, aby można było przeanalizować jego dyskretne kroki w debugerze. Umieszcza również `for` pętlę w funkcji i uruchamia ją `main` jawnie, wywołując tę funkcję:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Sprawdź, czy kod działa prawidłowo, naciskając **klawisz F5** lub wybierając polecenie menu   >  **Debuguj rozpocznij** debugowanie. To polecenie uruchamia kod w debugerze, ale ponieważ nie zostało wykonane nic, aby wstrzymać program, gdy jest uruchomiony, po prostu drukuje wzorzec falowy dla kilku iteracji. Naciśnij dowolny klawisz, aby zamknąć okno danych wyjściowych.

    > [!Tip]
    > Aby automatycznie zamknąć okno danych wyjściowych po zakończeniu pracy programu, wybierz polecenie menu Narzędzia Opcje, rozwiń węzeł Python, wybierz pozycję Debugowanie , a następnie wyczyść opcję Zaczekaj na dane wejściowe, gdy proces  >   zakończy się **normalnie:**  
    >
    > ![Opcja debugowania języka Python w celu zamknięcia okna danych wyjściowych przy normalnym zamykaniu programu](media/vs-getting-started-python-22-debugging5.png)
    >
    > Aby uzyskać dodatkowe informacje na temat debugowania, w tym zadania, takie jak ustawianie argumentów interpretera i skryptu, zobacz [Debugowanie kodu w języku Python](debugging-python-in-visual-studio.md).

1. Ustaw punkt przerwania w instrukcji, klikając raz na szarym marginesie przy tym wierszu lub umieszczając karet w tym wierszu i używając polecenia `for`   >  **Debuguj** przełącznik punktu przerwania **(F9).** Czerwona kropka pojawia się na szarym marginesie, aby wskazać punkt przerwania (zgodnie ze strzałką poniżej):

    ![Ustawianie punktu przerwania](media/vs-getting-started-python-18-debugging1.png)

1. Uruchom debuger ponownie **(F5)** i zobacz, że uruchomienie kodu zatrzymuje się w wierszu z tym punktem przerwania. W tym miejscu możesz sprawdzić stos wywołań i zbadać zmienne. Zmienne, które znajdują się w zakresie, są wyświetlane w **oknie Automatyczne** podczas ich definiowania; Możesz również przełączyć  się do widoku Zmienne lokalne w dolnej części tego okna, aby wyświetlić wszystkie zmienne, które Visual Studio w bieżącym zakresie (w tym funkcje), nawet przed ich definicją:

    ![Środowisko interfejsu użytkownika punktu przerwania dla języka Python](media/vs-getting-started-python-19-debugging2b.png)

1. Obserwuj pasek narzędzi debugowania (pokazany poniżej) u góry Visual Studio okna. Ten pasek narzędzi zapewnia szybki dostęp do najbardziej typowych poleceń debugowania (które można również znaleźć w menu **Debugowanie):**

    ![Przyciski podstawowych pasków narzędzi debugowania](media/vs-getting-started-python-20-debugging3.png)

    Przyciski od lewej do prawej:
    - **Kontynuuj** (**F5**) uruchamia program do następnego punktu przerwania lub do zakończenia programu.
    - **Break All** **(Ctrl** + **Alt** + **Break**) wstrzymuje długotrwały program.
    - **Zatrzymaj** **debugowanie (Shift** F5 ) zatrzymuje program w dowolnym miejscu + i zamyka debuger.
    - **Uruchom** ponownie **(Ctrl** Shift F5 ) zatrzymuje program wszędzie tam, gdzie jest, i uruchamia go ponownie +  + od początku w debugerze.
    - **Show Next Statement** **(Alt** + **Num** **&#42;**) przełącza się do następnego wiersza kodu do uruchomienia. Jest to najbardziej przydatne, gdy poruszasz się po kodzie podczas sesji debugowania i chcesz szybko wrócić do punktu, w którym debuger jest wstrzymany.
    - **Step Into** (**F11**) uruchamia następny wiersz kodu, wprowadzając do wywołanych funkcji.
    - **Funkcja Step Over** **(F10)** uruchamia następny wiersz kodu bez wprowadzania do wywołanych funkcji.
    - **Step Out** **(Shift** + **F11**) uruchamia pozostałą część bieżącej funkcji i wstrzymuje się w kodzie wywołującym.

1. Przekłoń `for` instrukcje przy **użyciu funkcji Step Over**. *Krokowe* oznacza, że debuger uruchamia bieżący wiersz kodu, w tym wszystkie wywołania funkcji, a następnie natychmiast wstrzymuje działanie. Zwróć uwagę, że `i` zmienna jest teraz zdefiniowana w **oknach Zmienne** lokalne **i** Automatyczne.

1. Przekń następny wiersz kodu, który wywołuje `make_dot_string` i wstrzymuje. **Krok powyżej** w szczególności oznacza, że debuger uruchamia całą część i wstrzymuje się `make_dot_string` po powrocie. Debuger nie zatrzymuje się wewnątrz tej funkcji, chyba że istnieje oddzielny punkt przerwania.

1. Kontynuuj wykonywanie kodu kilka razy i obserwuj zmiany  wartości w oknie Ustawienia **lokalne** lub Automatyczne.

1. W **oknie Zmienne** lokalne lub **Automatyczne** kliknij dwukrotnie kolumnę **Wartość** dla zmiennych lub , `i` aby `s` edytować wartość. Naciśnij **klawisz Enter** lub kliknij dowolny obszar poza wartością, aby zastosować zmiany.

1. Kontynuuj wykonywanie krokowe kodu, korzystając **z funkcji Step Into**. **Krok do** oznacza, że debuger wchodzi do dowolnego wywołania funkcji, dla którego zawiera informacje debugowania, takie jak `make_dot_string` . Wewnątrz `make_dot_string` możesz przeanalizować zmienne lokalne i przejść przez jego kod.

1. Kontynuuj wykonywanie **krokowe** za pomocą kroku Do i zwróć uwagę, że po osiągnięciu końca kroku następny krok powraca do pętli z nową wartością `make_dot_string` `for` zwracaną w `s` zmiennej . Po kolejnym kroku do instrukcji zwróć uwagę, że funkcja `print` **Step Into** on nie wchodzi do `print` tej funkcji. Wynika to z `print` tego, że nie jest on napisany w języku Python, ale jest raczej kodem natywnym w środowisku uruchomieniowym języka Python.

1. Kontynuuj korzystanie **z funkcji Step Into** do momentu, aż ponownie przejdą do kroku `make_dot_string` . Następnie użyj **funkcji Step Out** i zwróć uwagę, że wrócisz do `for` pętli. W **przypadku funkcji Step Out** debuger uruchamia pozostałą część funkcji, a następnie automatycznie wstrzymuje działanie w wywołującym kodzie. Jest to bardzo przydatne, gdy przechodzisz przez część długiej funkcji, którą chcesz debugować, ale nie musisz przechodzić przez resztę i nie chcesz ustawiać jawnego punktu przerwania w kodzie wywołującym.

1. Aby kontynuować uruchamianie programu do momentu, gdy zostanie osiągnięty następny punkt przerwania, użyj **klawisza Kontynuuj** **(F5).** Ponieważ w pętli jest punkt `for` przerwania, należy przerwać następną iterację.

1. Wykonywanie krokowe setek iteracji pętli może być pracochłonne, Visual Studio więc można dodać *warunek* do punktu przerwania. Debuger następnie wstrzymuje program w punkcie przerwania tylko wtedy, gdy warunek jest spełniony. Na przykład można użyć warunku z punktem przerwania w instrukcji , aby wstrzymać ją tylko wtedy, gdy wartość `for` `i` przekracza 1600. Aby ustawić ten warunek, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania i wybierz **pozycję Warunki** **(Alt** + **F9**  >  **C).** W **wyświetlonym oknie** podręcznym Ustawienia punktu przerwania wprowadź jako wyrażenie i `i > 1600` wybierz pozycję **Zamknij.** Naciśnij **klawisz F5,** aby kontynuować i zauważ, że program uruchamia wiele iteracji przed następnym podziałem.

    ![Ustawianie warunku punktu przerwania](media/vs-getting-started-python-21-debugging4.png)

1. Aby uruchomić program do ukończenia, wyłącz punkt przerwania, klikając prawym przyciskiem myszy kropkę na marginesie i wybierając polecenie **Wyłącz** punkt przerwania **(Ctrl** + **F9).** Następnie wybierz **pozycję Kontynuuj** (lub naciśnij **klawisz F5),** aby uruchomić program. Po zakończeniu działania programu program Visual Studio sesję debugowania i wróci do trybu edycji. Należy pamiętać, że punkt przerwania można również usunąć, wybierając jego kropkę lub klikając prawym przyciskiem myszy kropkę i wybierając polecenie Usuń punkt przerwania **,** ale spowoduje to również usunięcie wszystkich ustawionych warunków.

> [!Tip]
> W niektórych sytuacjach, na przykład w przypadku awarii samego interpretera języka Python, okno danych wyjściowych może pojawić się tylko na krótko, a następnie automatycznie zamknąć bez możliwości zobaczenia komunikatów o błędach. W takim przypadku kliknij prawym przyciskiem myszy projekt w oknie Eksplorator rozwiązań pozycję **Właściwości,** wybierz kartę **Debugowanie,** a następnie dodaj do pola `-i` **Argumenty interpretera.** Ten argument powoduje, że interpreter przejść w tryb interaktywny po zakończeniu działania programu, dzięki czemu okno będzie otwarte do momentu wciśniętego **klawisza Ctrl** + **Z**  >  **Enter,** aby zakończyć działanie.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Instalowanie pakietów w środowisku języka Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Głębiej

- [Debugowanie](debugging-python-in-visual-studio.md)
- [Debugowanie w Visual Studio](../debugger/debugger-feature-tour.md) zapewnia pełną dokumentację Visual Studio funkcji debugowania programu .
