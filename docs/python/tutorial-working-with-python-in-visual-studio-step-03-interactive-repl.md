---
title: Samouczek Python w programie Visual Studio, krok 3, interaktywny REPL
titleSuffix: ''
description: Krok 3 podstawowe Przewodnik po funkcjach języka Python w programie Visual Studio, obejmujący okno interaktywnej wizualizacji Python REPL.
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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986218"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3. Korzystanie z okna interaktywnego REPL

**Poprzedni krok: [pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Okno **interaktywne** programu Visual Studio dla języka Python zawiera bogate środowisko REPL (Read-oszacować-Print-pętle), które znacznie skraca typowy cykl Edit-Build-Debug. Okno **interaktywne** zapewnia wszystkie możliwości środowiska REPL w wierszu polecenia języka Python. Ułatwia ona również wymianę kodu z plikami źródłowymi w edytorze programu Visual Studio, które w przeciwnym razie są kłopotliwe w wierszu polecenia.

> [!NOTE]
> W przypadku problemów z usługą REPL upewnij się, że zainstalowano pakiety `ipython` i `ipykernel`, a aby uzyskać pomoc dotyczącą instalowania pakietów, zobacz [kartę pakiety środowiska Python](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Otwórz okno **interaktywne** , klikając prawym przyciskiem myszy środowisko Python projektu w **Eksplorator rozwiązań** (na przykład **Python 3,6 (32-bit)** , jak pokazano na poprzedniej ilustracji, a następnie wybierając polecenie **Otwórz okno interaktywne**. Możesz wybrać opcję **wyświetl** >  inne interaktywne okna środowiska**Python** **Windows** >  z głównego menu programu Visual Studio.

1. Okno **interaktywne** otwiera się pod edytorem za pomocą wiersza polecenia REPL języka Python standardowego **>>>** . Lista rozwijana **środowisko** umożliwia wybranie określonego interpretera do pracy z programem. Często chcesz również sprawić, aby okno **interaktywne** było większe, co można zrobić, przeciągając separator między dwoma oknami:

    ![Okno interaktywne języka Python i przeciąganie do rozmiaru](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Można zmienić rozmiar wszystkich okien w programie Visual Studio, przeciągając separatory obramowania. Możesz również przeciągać okna poza ramkę programu Visual Studio, a następnie rozmieścić je w obrębie ramki. Aby uzyskać szczegółowe informacje, zobacz [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

1. Wprowadź kilka instrukcji, takich jak `print("Hello, Visual Studio")` i wyrażeń, takich jak `123/456`, aby zobaczyć natychmiastowe wyniki:

    ![Natychmiastowe wyniki interaktywnego okna języka Python](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu pisania instrukcji wielowierszowej, takiej jak definicja funkcji, okno **interaktywne** pokazuje, że w języku Python **...** zostanie wyświetlony monit o kontynuowanie wierszy, które w przeciwieństwie do REPL wiersza polecenia, udostępnia Automatyczne wcięcia:

    ![Okno interaktywne języka Python z kontynuacją instrukcji](media/vs-getting-started-python-13-interactive3.png)

1. Okno **interaktywne** zawiera pełną historię wszystkich wprowadzonych elementów i usprawnia REPL wiersza polecenia z wielowierszowymi elementami historii. Na przykład można łatwo odwołać całą definicję funkcji `f` jako pojedynczą jednostkę i łatwo zmienić nazwę na `make_double`, zamiast tworzyć ją od nowa wiersz.

1. Program Visual Studio może wysyłać wiele wierszy kodu z okna edytora do okna **interaktywnego** . Ta funkcja pozwala zachować kod w pliku źródłowym i w łatwy sposób wysyłać wybrane części do okna **interaktywnego** . Następnie można pracować z takimi fragmentami kodu w szybkim środowisku REPL, zamiast uruchamiać cały program. Aby wyświetlić tę funkcję, najpierw Zastąp pętlę `for` w pliku *PythonApplication1.py* następującym:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz instrukcje `import`, `from`i `make_dot_string` funkcji w pliku *. PR* , kliknij prawym przyciskiem myszy i wybierz polecenie **Wyślij do interaktywnego** (lub naciśnij klawisz **Ctrl**+**Enter**). Fragment kodu zostanie natychmiast wklejony do okna **interaktywnego** i uruchomiony. Ponieważ kod definiuje funkcję, można szybko przetestować tę funkcję, wywołując ją kilka razy:

    ![Wysyłanie kodu do okna interaktywnego i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Użycie **klawisza Ctrl**+**Enter** w edytorze *bez* zaznaczenia powoduje uruchomienie bieżącego wiersza kodu w oknie **interaktywnym** i automatyczne umieszczenie karetki w następnym wierszu. Przy użyciu tej funkcji naciśnięcie **klawiszy Ctrl**+**wprowadza** się wielokrotnie, aby wygodnie wykonać krokowo kod, który nie jest możliwy tylko w wierszu polecenia języka Python. Umożliwia również przechodzenie przez kod bez uruchamiania debugera i bez konieczności uruchamiania programu od początku.

1. Możesz również kopiować i wklejać wiele wierszy kodu do okna **interaktywnego** z dowolnego źródła, takiego jak fragment kodu, który trudno wykonać przy użyciu wiersza polecenia języka Python REPL. W przypadku wklejenia okna **interaktywnego** uruchamiany jest ten kod, tak jakby został wprowadzony w:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu przy użyciu interaktywnego wysyłania](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa prawidłowo, ale jego dane wyjściowe nie są bardzo inspirujące. Inna wartość kroku w pętli `for` spowoduje wyświetlenie większej liczby cosinusów. Na szczęście, ponieważ cała pętla `for` znajduje się w historii REPL jako jedna jednostka, można łatwo wrócić i wprowadzić dowolne zmiany, a następnie ponownie przetestować funkcję. Naciśnij strzałkę w górę, aby najpierw odwołać pętlę `for`. Następnie naciśnij strzałkę w lewo lub w prawo, aby rozpocząć nawigowanie w kodzie (do momentu, gdy tak zrobisz, strzałki w górę i w dół kontynuują przechodzenie między historiami). Przejdź do i Zmień specyfikację `range` na `range(0, 360, 12)`. Następnie naciśnij klawisz **Ctrl**+**Enter** (gdziekolwiek w kodzie), aby ponownie uruchomić całą instrukcję:

    ![Edytowanie poprzedniej instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtórz ten proces, aby eksperymentować z różnymi ustawieniami kroku do momentu znalezienia wartości, która ma być Najlepsza. Można również powtórzyć operację Wave przez wydłużenie zakresu, na przykład `range(0, 1800, 12)`.

1. Gdy nastąpi zapisanie kodu w oknie **interaktywnym** , zaznacz go, kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj kod** (**Ctrl**+**SHIFT**+**C**), a następnie wklej do edytora. Zwróć uwagę, jak ta specjalna funkcja programu Visual Studio automatycznie pomija wszystkie dane wyjściowe oraz `>>>` i `...`. Na przykład poniższy obraz pokazuje przy użyciu polecenia **Kopiuj kod** dla zaznaczenia zawierającego instrukcje i dane wyjściowe:

    ![Okno interaktywne Kopiuj polecenie kodu przy zaznaczaniu z instrukcjami i danymi wyjściowymi](media/vs-getting-started-python-17-interactive7.png)

    Po wklejeniu do edytora otrzymujesz tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować dokładną zawartość okna **interaktywnego** , w tym informacje o komunikatach i danych wyjściowych, po prostu Użyj standardowego polecenia **copy** .

1. Właśnie gotowe środowisko jest używane przez szybkie REPL środowiska **interaktywnego** w celu wypróbowania szczegółowych informacji o małym fragmencie kodu, a następnie dodaliśmy ten kod do pliku źródłowego projektu. Po ponownym uruchomieniu kodu przy użyciu **kombinacji klawiszy Ctrl**+**F5** (lub **debugowania** > **Uruchom bez debugowania**) zobaczysz dokładne wyniki.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Korzystanie z okna interaktywnego](python-interactive-repl-in-visual-studio.md)
- [Korzystanie z IPython REPL](interactive-repl-ipython.md)
