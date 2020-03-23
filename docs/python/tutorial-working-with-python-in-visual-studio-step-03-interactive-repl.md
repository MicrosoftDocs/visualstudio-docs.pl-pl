---
title: Python w programie Visual Studio krok 3, interaktywny REPL
titleSuffix: ''
description: Krok 3 podstawowego przewodnika po możliwościach języka Python w programie Visual Studio, obejmujący okno INTERAKCYJNE REPL języka Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986218"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3: Użyj interaktywnego okna REPL

**Poprzedni krok: [Napisz i uruchom kod](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Okno **interaktywne** programu Visual Studio dla języka Python zapewnia bogate środowisko pętli odczytu i oceny wydruku (REPL), które znacznie skraca zwykły cykl edit-build-debug. Okno **Interaktywne** udostępnia wszystkie możliwości środowiska REPL wiersza polecenia Języka Python. To również sprawia, że bardzo łatwo wymienić kod z plikami źródłowymi w edytorze programu Visual Studio, co w przeciwnym razie jest uciążliwe z wierszem polecenia.

> [!NOTE]
> Aby uzyskać problemy z REPL, upewnij się, że masz `ipython` zainstalowane i `ipykernel` pakiety, a pomoc w instalowaniu pakietów, zobacz [zakładkę Pakiety środowisk Pythona](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Otwórz okno **Interaktywne,** klikając prawym przyciskiem myszy środowisko Python projektu w **Eksploratorze rozwiązań** (na przykład **Python 3.6 (32-bit)** pokazany na wcześniejszej grafice) i wybierając **polecenie Otwórz okno interaktywne**. Z głównego menu programu Visual Studio można wybrać opcję **Wyświetl** > **inne** > **interaktywne systemy Windows Python.**

1. Okno **Interaktywne** otwiera się pod **>>>** edytorem ze standardowym monitem OPL języka Python. Lista rozwijana **Środowisko** umożliwia wybranie określonego interpretera do pracy. Często chcesz również pomniejszyć okno **Interaktywne,** co można zrobić, przeciągając separator między dwoma oknami:

    ![Interaktywne okno języka Python i przeciąganie w celu zmienić rozmiar](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Można zmienić rozmiar wszystkich okien w programie Visual Studio, przeciągając separatory obramowania. Można również przeciągnąć okna niezależnie od ramki programu Visual Studio i zmienić ich kolejność w odpowiednim czasie w ramce. Aby uzyskać pełne informacje, zobacz [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

1. Wprowadź kilka instrukcji, takich `print("Hello, Visual Studio")` `123/456` jak i wyrażenia, jak zobaczyć natychmiastowe wyniki:

    ![Interaktywne okno Pythona natychmiastowe wyniki](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu pisania instrukcji wielowierszowej, takiej jak definicja funkcji, w oknie **Interactive** jest wyświetlany monit Pythona **...** o kontynuowaniu wierszy, który w przeciwieństwie do wiersza polecenia REPL zapewnia automatyczne wcięcie:

    ![Interaktywne okno Pythona z kontynuacją instrukcji](media/vs-getting-started-python-13-interactive3.png)

1. Okno **Interaktywne** zawiera pełną historię wszystkiego, co wprowadzono, i poprawia na wierszu polecenia REPL z elementami historii wielowierszowej. Na przykład można łatwo przywołać całą `f` definicję funkcji jako pojedynczej `make_double`jednostki i łatwo zmienić nazwę na , zamiast ponownie utworzyć wiersz po wierszu funkcji.

1. Visual Studio może wysyłać wiele wierszy kodu z okna edytora do okna **interaktywne.** Ta funkcja umożliwia przechowywanie kodu w pliku źródłowym i łatwe wysyłanie wybranych jego części do okna **Interaktywne.** Następnie można pracować z takich fragmentów kodu w środowisku szybkiego REPL, a nie konieczności uruchamiania całego programu. Aby wyświetlić tę funkcję, najpierw zastąp pętlę `for` w pliku *PythonApplication1.py* następującymi elementami:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz `import`, `from`i `make_dot_string` instrukcje funkcji w pliku *py,* kliknij prawym przyciskiem myszy i wybierz polecenie **Wyślij do interaktywnej** (lub naciśnij klawisz **Ctrl**+**Enter**). Fragment kodu jest natychmiast wklejany do **interakcyjnego** okna i uruchamiany. Ponieważ kod zdefiniował funkcję, można szybko przetestować tę funkcję, wywołując ją kilka razy:

    ![Wysyłanie kodu do interaktywnego okna i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Za pomocą **klawisza Ctrl**+**Enter** w edytorze *bez* zaznaczenia uruchamia bieżący wiersz kodu w oknie **Interaktywna** i automatycznie umieszcza lecszę w następnym wierszu. Dzięki tej funkcji naciśnięcie **klawisza Ctrl**+**Enter** zapewnia wygodny sposób przechodzenia przez kod, który nie jest możliwy tylko w wierszu polecenia Języka Python. Umożliwia również krok po kroku kodu bez uruchamiania debugera i bez konieczności uruchamiania programu od początku.

1. Można również skopiować i wkleić wiele wierszy kodu do okna **Interaktywne** z dowolnego źródła, takiego jak fragment kodu poniżej, co jest trudne do wykonania w wierszu polecenia Języka Python REPL. Po wklejeniu okno **Interaktywne** uruchamia ten kod tak, jakby wpisano go w:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu przy użyciu funkcji Wysyłanie interakcyjne](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa dobrze, ale jego dane wyjściowe nie jest bardzo inspirujące. Inna wartość kroku `for` w pętli pokaże więcej fali cosine. Na szczęście, ponieważ `for` cała pętla znajduje się w historii REPL jako pojedyncza jednostka, łatwo jest wrócić i wprowadzić wszelkie zmiany, które chcesz, a następnie ponownie przetestować funkcję. Naciśnij strzałkę w górę, aby najpierw przywołać pętlę. `for` Następnie naciśnij strzałki w lewo lub w prawo, aby rozpocząć nawigację w kodzie (dopóki tego nie zrobisz, strzałki w górę i w dół będą przechodzić przez historię). Przejdź do specyfikacji `range` `range(0, 360, 12)`i zmień jej na . Następnie naciśnij **klawisze Ctrl**+**Enter** (w dowolnym miejscu w kodzie), aby ponownie uruchomić całą instrukcję:

    ![Edytowanie poprzedniej instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtórz proces, aby eksperymentować z różnymi ustawieniami kroków, aż znajdziesz wartość, która najbardziej Ci się podoba. Można również powtórzyć falę, wydłużając zakres, `range(0, 1800, 12)`na przykład .

1. Gdy kod jest zadowalający, zaznacz go w oknie **Interaktywnym,** zaznacz go, kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj kod** **(Ctrl**+**Shift**+**C),** a następnie wklej do edytora. Zwróć uwagę, jak ta specjalna funkcja programu Visual Studio `>>>` automatycznie `...` pomija wszelkie dane wyjściowe, a także monity i monity. Na przykład poniższy obraz ekspozycyjny przedstawia polecenie **Kopiuj kod** w zaznaczeniu, które zawiera monity i dane wyjściowe:

    ![Interaktywne polecenie kopiowania okna na zaznaczeniu z monitami i wyjściami](media/vs-getting-started-python-17-interactive7.png)

    Po wklejeniu do edytora otrzymujesz tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować dokładną zawartość okna **Interaktywne,** w tym monity i dane wyjściowe, po prostu użyj standardowego polecenia **Kopiuj.**

1. Co właśnie zrobiłeś, to użyć szybkiego środowiska REPL w oknie **Interaktywne,** aby wypracować szczegóły dla małego fragmentu kodu, a następnie wygodnie dodał ten kod do pliku źródłowego projektu. Po ponownym uruchomieniu kodu z **Ctrl**+**F5** (lub **Debug** > **start bez debugowania),** zobaczysz dokładne wyniki, które chcesz.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Głębiej

- [Korzystanie z okna Interaktywne](python-interactive-repl-in-visual-studio.md)
- [Korzystanie z iPython REPL](interactive-repl-ipython.md)
