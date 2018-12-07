---
title: Język Python w programie Visual Studio — samouczek krok 3, interaktywny REPL
titleSuffix: ''
description: Krok 3 przewodnika podstawowe funkcje języka Python w programie Visual Studio, obejmujących okna interaktywnego REPL języka Python.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7f237dde510ad9fd65416ae7521ebeed705781c2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066122"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3: Korzystanie z okna interaktywnego REPL

**Poprzedni krok: [pisania i uruchamiania kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Visual Studio **Interactive** okna dla języka Python zapewnia rozbudowane odczytu — ocena print-loop (REPL) który znacznie skraca zwykle cyklu Edycja--kompilacja--debugowanie. **Interactive** okna oferuje wszystkie funkcje środowiska REPL wiersza polecenia języka Python. Zapewnia także ją łatwo wymienić kod przy użyciu plików źródłowych w programie Visual Studio edytora, które w przeciwnym razie jest kłopotliwe przy użyciu wiersza polecenia.

1. Otwórz **Interactive** okna, klikając prawym przyciskiem myszy projekt środowiska Python w **Eksploratora rozwiązań** (takie jak **środowiska Python 3.6 (32-bitowy)** pokazano na rysunku wcześniej) i Wybieranie **Otwórz okno interaktywne**. Możesz też wybrać **widoku** > **Windows inne** > **Windows Interactive Python** z głównego menu programu Visual Studio.

1. **Interactive** poniżej edytora ze standardem zostanie otwarte okno **>>>** REPL języka Python w wierszu polecenia. **Środowiska** listy rozwijanej można wybrać określonych interpreter chcesz pracować. Często też mają być **Interactive** okna większe, co można zrobić, przeciągając separator między dwoma oknami:

    ![Oknie interakcyjnym środowiska Python i przeciągając do zmiany rozmiaru](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Możesz zmienić rozmiar wszystkich okien w programie Visual Studio, przeciągając granicznych separatorów. Można również przeciągnij windows niezależnie od ramek programu Visual Studio i ich rozmieszczenia, jednak wewnątrz ramki, takich jak. Aby uzyskać szczegółowe informacje, zobacz [dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

1. Wprowadź kilka instrukcji takich jak `print("Hello, Visual Studio")` i wyrażeń, takich jak `123/456` aby zobaczyć wyniki wprowadzenia:

    ![Wyniki wprowadzenia okno interaktywne języka Python](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu pisania wielowierszowy instrukcji, takie jak definicja funkcji **Interactive** okno pokazuje języka Python **...**  wybór opcji Monituj o kontynuowanie wiersze, której w przeciwieństwie do wiersza polecenia REPL, oferuje automatyczne wcięcie:

    ![Okno interaktywne języka Python za pomocą instrukcji kontynuacji](media/vs-getting-started-python-13-interactive3.png)

1. **Interactive** okna zapewnia pełną historię wszystkich wprowadzono i poprawia REPL wiersza polecenia, za pomocą elementów historii wielowierszowe. Na przykład łatwe Wycofaj całą definicję `f` działać jako pojedynczą jednostkę, a następnie łatwo zmienić nazwę aby `make_double`, zamiast ponownego utworzenia funkcji wiersz po wierszu.

1. Program Visual Studio może wysyłać wielu wierszy kodu z okna edytora, aby **Interactive** okna. Ta funkcja umożliwia utrzymanie kodu w pliku źródłowym i umożliwia łatwe przesyłanie Wybieranie części go do **Interactive** okna. Następnie można pracować przy użyciu tych fragmentów kodu w szybkiej środowisko REPL zamiast konieczności uruchamiania całego programu. Aby wyświetlić tę funkcję, należy najpierw Zastąp `for` pętli w *PythonApplication1.py* pliku następującym kodem:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz tylko `import` i `from` instrukcji w *.py* pliku, kliknij prawym przyciskiem myszy i wybierz **Wyślij do środowiska interaktywnego** (lub naciśnij **Ctrl** + **Wprowadź**). Fragment kodu natychmiast jest wklejany do **Interactive** okna i uruchom. Teraz wybierz `make_dot_string` działać, a następnie powtórz tego samego polecenia, które ponownie uruchomi ten fragment kodu. Ponieważ kod definiuje funkcję, możesz szybko przetestować tę funkcję, wywołując kilka razy:

    ![Wysyłanie kodu do okna interaktywnego i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Za pomocą **Ctrl**+**Enter** w edytorze *bez* wyboru uruchamia bieżącego wiersza kodu w **Interactive** okno i automatycznie przełącza karetkę w następnym wierszu. Dzięki tej funkcji naciskając klawisz **Ctrl**+**Enter** wielokrotnie oferuje wygodny sposób, aby przejść przez swój kod, który nie jest możliwe przy użyciu wiersza polecenia języka Python. Dzięki temu można także przejść przez kod, bez konieczności uruchamiania debugera i niekoniecznie uruchamiania programu od samego początku.

1. Można również skopiować i wkleić wiele wierszy kodu w **Interactive** okno z dowolnego źródła, takich jak poniższy, fragment kodu, które jest trudno jest wykonać za pomocą replikacja wiersza polecenia języka Python Po wklejeniu **Interactive** okno uruchamia kod tak, jakby wpisał go:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu za pomocą wysyłania interaktywne](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa poprawnie, ale jego dane wyjściowe nie jest bardzo inspirujących. Krok różne wartości w `for` pokazywałaby więcej wave cosinus pętli. Na szczęście ponieważ cały `for` pętli znajduje się w historii REPL jako pojedyncza jednostka, można łatwo Przejdź wstecz i wprowadzanie niezależnie od zmian możesz chcieć i następnie w celu przetestowania funkcji ponownie. Naciśnij strzałkę w górę do pierwszego wycofywania `for` pętli. Następnie naciśnij klawisz strzałki lewej lub prawej, aby rozpocząć nawigowanie w kodzie (do czasu w tym celu w górę i strzałki w dół w dalszym ciągu przechodzić między historii). Przejdź do, a następnie zmień `range` specyfikacja `range(0, 360, 12)`. Następnie naciśnij klawisz **Ctrl**+**Enter** (w dowolnym miejscu kodu) aby uruchomić ponownie całą instrukcję:

    ![Edytowanie poprzednich instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtórz te czynności, aby eksperymentować z kroku różne ustawienia, do momentu znalezienia wartości, które najlepiej. Można również ustawić etapy powtórzeń wydłużyć zakresu, na przykład `range(0, 1800, 12)`.
 
1. Po zakończeniu kodu są napisane w **Interactive** okna, wybierz go, kliknij prawym przyciskiem myszy i wybierz **Kopiuj kod** (**Ctrl** + **Shift**+**C**), a następnie wklej w edytorze. Zwróć uwagę, jak to specjalnej funkcji programu Visual Studio automatycznie pomija żadnych danych wyjściowych, jak również `>>>` i `...` monity. Na przykład na poniższej ilustracji przedstawiono przy użyciu **Kopiuj kod** na wybór zawiera monity i dane wyjściowe polecenia:

    ![Okno interaktywne kopiowania kodu polecenie wyboru z monitami i danych wyjściowych](media/vs-getting-started-python-17-interactive7.png)

    Podczas wklejania do edytora spowoduje wyświetlenie tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować zawartość dokładnie **Interactive** okna, w tym monity i danych wyjściowych, wystarczy użyć standardowego **kopiowania** polecenia.

1. Co właśnie wykonano jest środowisko REPL szybkie **Interactive** okna pozwolimy na opracowanie szczegóły niewielkim fragmentem kodu, wygodnie dodawana kod do pliku źródłowego projektu. Gdy teraz uruchomić kod ponownie, używając **Ctrl**+**F5** (lub **debugowania** > **Uruchom bez debugowania**), możesz Zobacz dokładne wyniki, których potrzebujesz.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Za pomocą okna interakcyjnego](python-interactive-repl-in-visual-studio.md)
- [Użyj środowiska IPython REPL](interactive-repl-ipython.md)
