---
title: Język Python w Visual Studio samouczku, krok 3, interaktywna aplikacja REPL
titleSuffix: ''
description: Krok 3 podstawowego przewodnika po możliwościach języka Python w języku Visual Studio, obejmującego okno interaktywnego środowiska REPL języka Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e82073b77231f84452ba51402f407904142bbf8e
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941100"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3. Korzystanie z okna interakcyjnego REPL

**Poprzedni krok: [Pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Okno Visual Studio **interactive** dla języka Python zapewnia rozbudowane środowisko repl (read-evaluate-print-loop), które znacznie skraca zwykły cykl edytowania i kompilowania/debugowania. Okno **Interaktywne** zapewnia wszystkie możliwości środowiska REPL wiersza polecenia języka Python. Ułatwia to również wymianę kodu z plikami źródłowymi w Visual Studio, co w przeciwnym razie jest kłopotliwe w przypadku wiersza polecenia.

> [!NOTE]
> W przypadku problemów z repl, upewnij się, że zainstalowano pakiety i , a aby uzyskać pomoc podczas instalowania pakietów, zobacz kartę Pakiety `ipython` `ipykernel` środowisk [Python](./python-environments-window-tab-reference.md#packages-tab).

1. Otwórz  okno Interaktywne, klikając prawym przyciskiem myszy środowisko języka Python projektu w programie **Eksplorator rozwiązań** (na przykład **Python 3.6 (32-bitowe)** pokazane na wcześniejszej grafice) i wybierając polecenie Otwórz okno **interaktywne.** Możesz też wybrać pozycję **Wyświetl** inne  >  **interaktywne okna Windows**  >  **Python** z głównego Visual Studio menu.

1. Okno **Interaktywne** zostanie otwarte poniżej edytora ze standardowym monitem **>>>** REPL języka Python. Lista **rozwijana** Środowisko umożliwia wybranie określonego interpretera do pracy. Często należy również powiększyć okno  Interaktywne, co można zrobić, przeciągając separator między dwoma oknami:

    ![Interaktywne okno języka Python i przeciąganie w celu zmiany rozmiaru](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Możesz zmienić rozmiar wszystkich okien w Visual Studio, przeciągając separatory obramowania. Możesz również przeciągać okna poza ramkę Visual Studio i zmieniać ich rozmieszczenie w taki sposób, jak chcesz. Aby uzyskać szczegółowe informacje, zobacz [Dostosowywanie układów okien.](../ide/customizing-window-layouts-in-visual-studio.md)

1. Wprowadź kilka instrukcji, takich jak `print("Hello, Visual Studio")` i , aby zobaczyć natychmiastowe `123/456` wyniki:

    ![Natychmiastowe wyniki okna interaktywnego języka Python](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu pisania instrukcji wieloliniowej,  na przykład definicji  funkcji, w oknie Interaktywny jest wyświetlany monit języka Python o kontynuowanie wierszy, który, w przeciwieństwie do wiersza polecenia REPL, zapewnia automatyczne wcięcie. Aby dodać nowy **wiersz ...,** naciśnij klawisz `Shift+Enter` :

    ![Interaktywne okno języka Python z kontynuacją instrukcji](media/vs-getting-started-python-13-interactive3.png)

1. Okno **Interaktywne** zawiera pełną historię wszystkich wprowadzonych elementów i ulepsza wiersz polecenia REPL z elementami historii wieloliniowej. Na przykład można łatwo przywołać całą definicję funkcji jako pojedynczą jednostkę i łatwo zmienić nazwę na , zamiast ponownie tworzyć funkcję wiersz `f` `make_double` po wierszu.

1. Visual Studio wysłać wiele wierszy kodu z okna edytora do okna **Interaktywne.** Ta funkcja umożliwia utrzymanie kodu w pliku źródłowym i łatwe wysyłanie wybranych jego części do okna **Interaktywne.** Następnie można pracować z takimi fragmentami kodu w szybkim środowisku REPL, zamiast uruchamiać cały program. Aby wyświetlić tę funkcję, najpierw zastąp `for` pętlę w *PythonApplication1.py* pliku następującym kodem:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz instrukcje funkcji , i w pliku `import` `from` `make_dot_string` *py.* Kliknij prawym przyciskiem myszy zaznaczony tekst i wybierz polecenie **Wyślij do interakcyjnego** (lub naciśnij klawisz **Ctrl** + **Enter**). Fragment kodu jest natychmiast wklejony w oknie **Interaktywny** i uruchamiany. Ponieważ kod zdefiniuje funkcję, możesz ją szybko przetestować, wywołując ją kilka razy:

    ![Wysyłanie kodu do okna interaktywnego i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Użycie **klawisza Ctrl** Enter w edytorze bez zaznaczenia uruchamia bieżący wiersz kodu w oknie Interaktywny i automatycznie umieszcza cyelek +  w następnym wierszu.   Dzięki tej funkcji wielokrotne naciśnięcie **klawisza Ctrl** Enter zapewnia wygodny sposób na krok po kodzie, który nie jest możliwy tylko w wierszu +  polecenia języka Python. Umożliwia ona również krok po kroku kod bez uruchamiania debugera i bez konieczności uruchamiania programu od początku.

1. Możesz również skopiować i wkleić  wiele wierszy kodu w oknie interaktywnym z dowolnego źródła, takiego jak poniższy fragment kodu, co jest trudne w przypadku środowiska REPL wiersza polecenia języka Python. Po wklejaniu okno **Interaktywne** uruchamia ten kod tak, jakby został wpisany w:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu przy użyciu opcji Wysyłanie interakcyjne](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa prawidłowo, ale jego dane wyjściowe nie są bardzo inspirujące. Inna wartość kroku w `for` pętli będzie pokazywać więcej cosine wave. Na szczęście, ponieważ cała pętla znajduje się w historii REPL jako pojedyncza jednostka, można łatwo wrócić i wprowadzić wszelkie zmiany, a następnie ponownie przetestować `for` funkcję. Naciśnij strzałkę w górę, aby najpierw odwołać `for` pętlę. Następnie naciskaj strzałki w lewo lub w prawo, aby rozpocząć nawigowanie po kodzie (dopóki nie zrobisz tego, strzałki w górę i w dół będą przechodzić przez historię). Przejdź do i zmień `range` specyfikację na `range(0, 360, 12)` . Następnie naciśnij **klawisz Ctrl** + **Enter** (w dowolnym miejscu w kodzie), aby ponownie uruchomić całą instrukcje:

    ![Edytowanie poprzedniej instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtarzaj ten proces, aby eksperymentować z różnymi ustawieniami kroków, aż znajdziesz najbardziej lubianą wartość. Falę można również powtórzyć, wydłużając zakres, na przykład `range(0, 1800, 12)` .

1. Jeśli kod pisany w oknie  Interaktywny jest zadowala, wybierz go. Następnie kliknij prawym przyciskiem myszy kod i wybierz polecenie **Kopiuj kod** **(Ctrl** + **Shift** + **C).** Na koniec wklej wybrany kod do edytora. Zauważ, że ta specjalna funkcja Visual Studio automatycznie pomija wszystkie dane wyjściowe, a także `>>>` `...` monity i . Na przykład na poniższej ilustracji przedstawiono użycie polecenia **Kopiuj** kod dla zaznaczenia, które zawiera monity i dane wyjściowe:

    ![okno Interactive skopiować kod po zaznaczeniu przy użyciu monitów i danych wyjściowych](media/vs-getting-started-python-17-interactive7.png)

    Po wklejeniu do edytora otrzymasz tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować dokładną  zawartość okna Interaktywne, w tym monity i dane wyjściowe, po prostu użyj standardowego **polecenia Kopiuj.**

1. To, co właśnie zrobiono, to użyć  szybkiego środowiska REPL okna interaktywnego, aby uzyskać szczegółowe informacje dotyczące małego fragmentu kodu, a następnie wygodnie dodać ten kod do pliku źródłowego projektu. Po uruchomieniu kodu ponownie za pomocą **klawiszy Ctrl** + **F5** (lub **Rozpocznij debugowanie** bez debugowania) zobaczysz konkretne  >  wyniki.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Głębiej

- [Korzystanie z okno Interactive](python-interactive-repl-in-visual-studio.md)
- [Korzystanie z IPython REPL](interactive-repl-ipython.md)