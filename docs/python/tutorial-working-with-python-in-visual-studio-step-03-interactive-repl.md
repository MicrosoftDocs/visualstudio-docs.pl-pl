---
title: Samouczek Python w programie Visual Studio, krok 3, interaktywny REPL
titleSuffix: ''
description: Krok 3 podstawowe Przewodnik po funkcjach języka Python w programie Visual Studio, obejmujący okno interaktywnej wizualizacji Python REPL.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c4ae447976798372e049df46552f8383389f7b3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920777"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3. Korzystanie z okna interaktywnego REPL

**Poprzedni krok: [pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Okno **interaktywne** programu Visual Studio dla języka Python zawiera bogate środowisko REPL (Read-oszacować-Print-pętle), które znacznie skraca typowy cykl Edit-Build-Debug. Okno **interaktywne** zapewnia wszystkie możliwości środowiska REPL w wierszu polecenia języka Python. Ułatwia ona również wymianę kodu z plikami źródłowymi w edytorze programu Visual Studio, które w przeciwnym razie są kłopotliwe w wierszu polecenia.

> [!NOTE]
> W przypadku problemów z programem REPL upewnij się, `ipython` że `ipykernel` zainstalowano pakiety i aby uzyskać pomoc dotyczącą instalowania pakietów, zobacz [kartę pakiety środowiska Python](./python-environments-window-tab-reference.md#packages-tab).

1. Otwórz okno **interaktywne** , klikając prawym przyciskiem myszy środowisko Python projektu w **Eksplorator rozwiązań** (na przykład **Python 3,6 (32-bit)** , jak pokazano na poprzedniej ilustracji, a następnie wybierając polecenie **Otwórz okno interaktywne**. Możesz wybrać opcję **Wyświetl**  >  **inne**  >  **interaktywne** okna środowiska Windows Python z głównego menu programu Visual Studio.

1. Okno **interaktywne** otwiera się poniżej edytora przy użyciu standardowego **>>>** monitu języka Python REPL. Lista rozwijana **środowisko** umożliwia wybranie określonego interpretera do pracy z programem. Często chcesz również sprawić, aby okno **interaktywne** było większe, co można zrobić, przeciągając separator między dwoma oknami:

    ![Okno interaktywne języka Python i przeciąganie do rozmiaru](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Można zmienić rozmiar wszystkich okien w programie Visual Studio, przeciągając separatory obramowania. Możesz również przeciągać okna poza ramkę programu Visual Studio, a następnie rozmieścić je w obrębie ramki. Aby uzyskać szczegółowe informacje, zobacz [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

1. Wprowadź kilka instrukcji, takich jak `print("Hello, Visual Studio")` i wyrażenia, takie jak `123/456` Aby zobaczyć natychmiastowe wyniki:

    ![Natychmiastowe wyniki interaktywnego okna języka Python](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu pisania instrukcji wielowierszowej, takiej jak definicja funkcji, okno **interaktywne** pokazuje, że w języku Python **...** zostanie wyświetlony monit o kontynuowanie wierszy, które w przeciwieństwie do REPL wiersza polecenia, udostępnia Automatyczne wcięcia:

    ![Okno interaktywne języka Python z kontynuacją instrukcji](media/vs-getting-started-python-13-interactive3.png)

1. Okno **interaktywne** zawiera pełną historię wszystkich wprowadzonych elementów i usprawnia REPL wiersza polecenia z wielowierszowymi elementami historii. Na przykład można łatwo odwołać całą definicję `f` funkcji jako pojedynczą jednostkę i łatwo zmienić nazwę na `make_double` , zamiast tworzyć ją od nowa wiersz po wierszu.

1. Program Visual Studio może wysyłać wiele wierszy kodu z okna edytora do okna **interaktywnego** . Ta funkcja pozwala zachować kod w pliku źródłowym i w łatwy sposób wysyłać wybrane części do okna **interaktywnego** . Następnie można pracować z takimi fragmentami kodu w szybkim środowisku REPL, zamiast uruchamiać cały program. Aby wyświetlić tę funkcję, najpierw Zastąp `for` pętlę w pliku *PythonApplication1.py* następującym:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz `import` instrukcje, `from` i `make_dot_string` funkcji w pliku *. PR* . Kliknij prawym przyciskiem myszy zaznaczony tekst i wybierz polecenie **Wyślij do interaktywne** (lub naciśnij klawisz **Ctrl** + **Enter**). Fragment kodu zostanie natychmiast wklejony do okna **interaktywnego** i uruchomiony. Ponieważ kod definiuje funkcję, można szybko przetestować tę funkcję, wywołując ją kilka razy:

    ![Wysyłanie kodu do okna interaktywnego i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Przy użyciu **klawisza Ctrl** + **Enter** w edytorze *bez* zaznaczenia uruchamia bieżący wiersz kodu w oknie **interaktywnym** i automatycznie umieszcza karetkę w następnym wierszu. W przypadku tej funkcji naciśnięcie klawisza **Ctrl** w +  sposób wielokrotnie zapewnia wygodny sposób na przechodzenie przez kod, który nie jest możliwy tylko przy użyciu wiersza polecenia języka Python. Umożliwia również przechodzenie przez kod bez uruchamiania debugera i bez konieczności uruchamiania programu od początku.

1. Możesz również kopiować i wklejać wiele wierszy kodu do okna **interaktywnego** z dowolnego źródła, takiego jak fragment kodu, który trudno wykonać przy użyciu wiersza polecenia języka Python REPL. W przypadku wklejenia okna **interaktywnego** uruchamiany jest ten kod, tak jakby został wprowadzony w:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu przy użyciu interaktywnego wysyłania](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa prawidłowo, ale jego dane wyjściowe nie są bardzo inspirujące. Inna wartość kroku w `for` pętli spowoduje wyświetlenie większej liczby cosinusów. Na szczęście cała `for` Pętla znajduje się w historii REPL jako pojedyncza jednostka, dlatego można ją łatwo wrócić i wprowadzić dowolne zmiany, a następnie ponownie przetestować funkcję. Naciśnij strzałkę w górę, aby najpierw odwołać `for` pętlę. Następnie naciśnij strzałkę w lewo lub w prawo, aby rozpocząć nawigowanie w kodzie (do momentu, gdy tak zrobisz, strzałki w górę i w dół kontynuują przechodzenie między historiami). Przejdź do i Zmień `range` specyfikację na `range(0, 360, 12)` . Następnie naciśnij klawisz **Ctrl** + **Enter** (gdziekolwiek w kodzie), aby ponownie uruchomić całą instrukcję:

    ![Edytowanie poprzedniej instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtórz ten proces, aby eksperymentować z różnymi ustawieniami kroku do momentu znalezienia wartości, która ma być Najlepsza. Można również powtórzyć operację Wave przez wydłużenie zakresu, na przykład `range(0, 1800, 12)` .

1. Gdy kod napisany w oknie **interaktywnym** jest zadowalający, wybierz go. Następnie kliknij prawym przyciskiem myszy kod, a następnie wybierz polecenie **Kopiuj kod** (**Ctrl** + **SHIFT** + **C**). Na koniec wklej wybrany kod do edytora. Zwróć uwagę na to, że Specjalna funkcja programu Visual Studio automatycznie pomija wszystkie dane wyjściowe, `>>>` a także instrukcje i `...` . Na przykład poniższy obraz pokazuje przy użyciu polecenia **Kopiuj kod** dla zaznaczenia zawierającego instrukcje i dane wyjściowe:

    ![Okno interaktywne Kopiuj polecenie kodu przy zaznaczaniu z instrukcjami i danymi wyjściowymi](media/vs-getting-started-python-17-interactive7.png)

    Po wklejeniu do edytora otrzymujesz tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować dokładną zawartość okna **interaktywnego** , w tym informacje o komunikatach i danych wyjściowych, po prostu Użyj standardowego polecenia **copy** .

1. Właśnie gotowe środowisko jest używane przez szybkie REPL środowiska **interaktywnego** w celu wypróbowania szczegółowych informacji o małym fragmencie kodu, a następnie dodaliśmy ten kod do pliku źródłowego projektu. Po ponownym uruchomieniu kodu za pomocą **klawisza Ctrl** + **F5** (lub **debugowania**  >  **Rozpocznij bez debugowania**) zobaczysz dokładne wyniki.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Korzystanie z okna interaktywnego](python-interactive-repl-in-visual-studio.md)
- [Korzystanie z IPython REPL](interactive-repl-ipython.md)