---
title: Wprowadzenie do samouczka R
description: Instruktaż przy użyciu języka R w programie Visual Studio, w tym tworzenie projektu, interaktywne okno, edycja kodu i debugowanie.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: df46a2731f9923d85a16082f96c44947099db592
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "63000507"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Wprowadzenie do programu R Tools for Visual Studio

Po zainstalowaniu narzędzia R Tools for Visual Studio (RTVS) (zobacz [Instalacja),](installing-r-tools-for-visual-studio.md)można szybko uzyskać smak środowiska, które zapewniają te narzędzia.

## <a name="create-an-r-project"></a>Tworzenie projektu R

1. Otwórz program Visual Studio.
1. Wybierz pozycję Nowy**New** > **projekt** **pliku** > **(Ctrl**+**Shift**+**N**)
1. Wybierz "Projekt R" w obszarze **Szablony** > **R**, nadaj projektowi nazwę i lokalizację, a następnie wybierz **przycisk OK:**

   ![Nowe okno dialogowe projektu dla języka R w programie Visual Studio (RTVS w programie VS2017)](media/getting-started-01-new-project.png)

1. Po utworzeniu projektu są wyświetlane następujące okna:

    - Po prawej stronie znajduje się Visual Studio Solution Explorer, gdzie można zobaczyć projekt wewnątrz *rozwiązania*zawierającego . (Rozwiązania mogą zawierać dowolną liczbę projektów różnych typów; szczegółowe informacje można znaleźć w [opisie projektów.](r-projects-in-visual-studio.md)
    - W lewym górnym rogu znajduje`script.R`się nowy plik Języka R ( ), w którym można edytować kod źródłowy za pomocą wszystkich funkcji edycji programu Visual Studio.
    - W lewym dolnym rogu znajduje się okno **R Interactive,** w którym można interaktywnie opracować i przetestować kod.

> [!Note]
> Można użyć okna **R Interactive** bez otwierania żadnych projektów, a nawet po załadowaniu innego typu projektu. Wystarczy wybrać **R Tools** > **Windows** > **R Interactive** w dowolnym momencie.

## <a name="explore-the-interactive-window-and-intellisense"></a>Poznaj interaktywne okno i intellisense

1. Sprawdź, czy okno interaktywne działa, wpisując wpis, `3 + 4` a następnie **wprowadź,** aby wyświetlić wynik:

    ![Okno interaktywne języka R w programie Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Wpisz coś trochę bardziej `ds <- c(1.5, 6.7, 8.9) * 1:12`skomplikowanego `ds` , a następnie wprowadź, aby zobaczyć wynik:

    ![Dodatkowy interaktywny przykład języka R w programie Visual Studio](media/getting-started-03-interactive2.png)

1. Wpisz, ale należy zauważyć, `m` że `me`zaraz po wpisaniu lub program Visual Studio IntelliSense udostępnia opcje automatycznego uzupełniania. `mean(ds)` Gdy żądane zakończenie zostanie zaznaczone na liście, naciśnij klawisz **Tab,** aby ją wstawić; zaznaczenie można zmieniać za pomocą klawiszy strzałek lub myszy.

    ![IntelliSense wyświetlane podczas wprowadzania kodu](media/getting-started-04-intellisense1.png)

1. Po zakończeniu `mean`wpisz nawias otwierający `(` i zwróć uwagę, jak IntelliSense zapewnia wbudowaną pomoc dla tej funkcji:

    ![IntelliSense pokazuje pomoc dla funkcji](media/getting-started-05-intellisense2.png)

1. Uzupełnij `mean(ds)` wiersz i naciśnij klawisz`[1] 39.51667`Enter, aby wyświetlić wynik ( ).

1. Okno Interaktywne jest zintegrowane z `?mean` pomocą, więc wprowadzenie wyświetla pomoc dla tej funkcji w oknie **Pomocy języka R** w programie Visual Studio. Aby uzyskać szczegółowe informacje, zobacz [Pomoc w narzędziach języka R dla programu Visual Studio](getting-started-help.md).

    ![Okno Pomocy języka R w programie Visual Studio](media/getting-started-06-help.png)

1. Niektóre polecenia, takie `plot(1:100)`jak , otwórz nowe okno w programie Visual Studio, gdy dane wyjściowe nie mogą być wyświetlane bezpośrednio w oknie interaktywnym:

    ![Wyświetlanie wykresu w programie Visual Studio](media/getting-started-07-plot-window.png)

Okno interaktywne umożliwia również przeglądanie historii, ładowanie i zapisywanie obszarów roboczych, dołączanie do debugera i interakcję z plikami kodu źródłowego zamiast przy użyciu kopiowania i wklejania. Zobacz [Praca z oknem interaktywnym R,](interactive-repl-for-r-in-visual-studio.md) aby uzyskać szczegółowe informacje.

## <a name="experience-code-editing-features"></a>Poznaj funkcje edycji kodu

Praca krótko z interaktywnym oknem pokazuje podstawowe funkcje edycji, takie jak IntelliSense, które działają również w edytorze kodu. Jeśli wprowadzisz ten sam kod, co poprzednio, zobaczysz te same monity automatycznego uzupełniania i IntelliSense, ale nie dane wyjściowe.

Pisanie kodu w *pliku . R* plik pozwala zobaczyć cały kod na raz i ułatwia wprowadzanie małych zmian, a następnie szybko zobaczyć wynik, uruchamiając kod w oknie interaktywnym. Można również mieć dowolną liczbę plików w projekcie. Gdy kod znajduje się w pliku, można również uruchomić go krok po kroku w debugerze (omówione w dalszej części tego artykułu). Te możliwości są przydatne podczas opracowywania algorytmów obliczeniowych i pisania kodu do manipulowania jednym lub więcej zestawów danych, zwłaszcza, gdy chcesz zbadać wszystkie wyniki pośrednie.

Na przykład poniższe kroki tworzą mały kod do zbadania [centralnego limitu (Wikipedia).](https://en.wikipedia.org/wiki/Central_limit_theorem) (Ten przykład został zaadaptowany na podstawie *książki kucharskiej R* Paula Teetora).

1. W `script.R` edytorze wprowadź następujący kod:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Aby szybko wyświetlić wyniki, zaznacz cały kod **(Ctrl**+**A),** a następnie naciśnij **klawisz Ctrl**+**Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie Wykonaj **w interaktywnym**. Cały wybrany kod jest uruchamiany w oknie interaktywnym tak, jakby wpisywał go bezpośrednio, pokazując wynik w oknie wydruku:

    ![Wyświetlanie wykresu w programie Visual Studio](media/getting-started-08-plot1.png)

1. W przypadku pojedynczego wiersza wystarczy nacisnąć klawisz **Ctrl**+**Enter** w dowolnym momencie, aby uruchomić ten wiersz w oknie interaktywnym.

> [!Tip]
> Poznaj wzór wprowadzania zmian i naciskania klawisza **Ctrl**+**Enter** (lub zaznaczania wszystkiego za pomocą **klawisza Ctrl**+**A,** a następnie naciśnięcia **klawisza Ctrl**+**Enter),** aby szybko uruchomić kod. Jest to znacznie bardziej wydajne niż używanie myszy do tych samych operacji.
>
> Ponadto można przeciągnąć i upuścić okno wydruku z ramki programu Visual Studio i umieścić je w dowolnym miejscu na ekranie. Następnie można zmienić rozmiar okna wydruku na żądane wymiary, a następnie zapisać je w pliku obrazu lub pliku PDF.

1. Dodaj kilka wierszy kodu, aby dołączyć drugi wykres:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Naciśnij **klawisze Ctrl**+**A** i **Ctrl**+**Enter** ponownie, aby uruchomić kod, uzyskując następujący wynik:

    ![Zaktualizowano podwójny wykres w programie Visual Studio](media/getting-started-09-plot2.png)

1. Problem polega na tym, że pierwszy wykres określa skalę `lines`pionową, więc drugi wykres (z ) nie pasuje. Aby rozwiązać ten problem, musimy `ylim` ustawić `plot` parametr na wywołanie, ale zrobić tak, że prawidłowo musimy dodać kod, aby obliczyć maksymalną wartość pionową. Wykonanie tego wiersza po wierszu w oknie interaktywnym jest niewygodne, ponieważ musimy `samp.means` zmienić kolejność kodu, aby użyć go przed wywołaniem `plot`. W pliku kodu możemy jednak łatwo wprowadzić odpowiednie zmiany:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **Ctrl**+**A** i **Ctrl**+**Wprowadź** ponownie, aby zobaczyć wynik:

    ![Zaktualizowano podwójny wykres w programie Visual Studio, skalowany poprawnie](media/getting-started-10-plot3.png)

Edytor może zrobić więcej. Aby uzyskać szczegółowe informacje, zobacz [Edytowanie kodu R](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md)i [fragmenty kodu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Debugowanie kodu

Jedną z głównych zalet programu Visual Studio jest jego debugowania interfejsu użytkownika. RTVS opiera się na tym silnym fundamencie i dodaje innowacyjny interfejs użytkownika, taki jak [Eksplorator zmiennych.](variable-explorer.md) W tym miejscu po prostu przyjrzyjmy się debugowaniu.

1. Aby rozpocząć, zresetuj bieżący obszar roboczy, aby wyczyścić wszystko, co zostało zrobione do tej pory, używając polecenia menu **R Tools** > **Session** > **Reset.** Domyślnie wszystko, co robisz w oknie interaktywnym, jest naliczane do bieżącej sesji, która jest następnie również używana przez debuger. Zresetowanie sesji, upewnij się, że sesja debugowania rozpoczyna się bez wcześniej istniejących danych. Reset **Reset** polecenia, jednak nie ma wpływu na *skrypt. R* pliku źródłowego, ponieważ jest zarządzany i zapisywany poza obszarem roboczym.

1. Ze *skryptem. R* plik utworzony w poprzedniej sekcji, ustawić punkt przerwania w wierszu, który zaczyna się `pop <-` od umieszczenia daszek w tym wierszu, a następnie naciskając klawisz **F9**lub wybierając polecenie menu **Debug** > **Toggle Breakpoint.** Alternatywnie, po prostu kliknij margines po lewej stronie (lub margines) dla tej linii, w której pojawia się czerwona kropka punkt przerwania:

    ![Ustawianie punktu przerwania w edytorze](media/getting-started-11-debug1.png)

1. Uruchom debuger z kodem w *skrypcie. R,* wybierając przycisk **Plik startowy źródła** na pasku narzędzi, wybierając pozycje menu**menu Pliku startowego Źródła** **debugowania** > lub naciskając **klawisz F5**. Visual Studio wchodzi w tryb debugowania i rozpoczyna uruchamianie kodu. Zatrzymuje się jednak w wierszu, w którym ustawiono punkt przerwania:

    ![Zatrzymywanie punktu przerwania w debugerze programu Visual Studio](media/getting-started-12-debug2.png)

1. Podczas debugowania visual studio zapewnia możliwość krok po wierszu kodu. Można również krok do funkcji, krok nad nimi, lub wyjść z nich do kontekstu wywołującego. Te możliwości, wraz z innymi, można znaleźć w menu **debugowania,** menu kontekstowym prawym przyciskiem myszy w edytorze i pasku narzędzi debugowania:

    ![Pasek narzędzi debugowania w programie Visual Studio](media/getting-started-13-debug3.png)

1. Po zatrzymaniu w punkcie przerwania, można sprawdzić wartości zmiennych. Znajdź okno **Autos** w programie Visual Studio i wybierz kartę wzdłuż dolnej części o nazwie **Locals**. Okno **Locals** pokazuje zmienne lokalne w bieżącym punkcie programu. Jeśli zostaniesz zatrzymany na zestaw punktów przerwania `pop` wcześniej, widać, że zmienna nie jest jeszcze zdefiniowana. Teraz użyj polecenia **Debug** > **Step Over** (**F10** `pop` ), a pojawi się wartość:

    ![Okno Dla mieszkańców w programie Visual Studio](media/getting-started-14-debug4.png)

1. Aby sprawdzić zmienne w różnych zakresach, w tym w zakresie globalnym i zakresach pakietów, użyj [Eksploratora zmiennych](variable-explorer.md). Eksplorator zmiennych umożliwia również przełączanie się do widoku tabelaryczne z kolumnami sortowalnymi i eksportowanie danych do pliku CSV.

    ![Rozszerzony widok Eksploratora zmiennych](media/variable-explorer-expanded-results.png)

1. Można kontynuować przechodzenie przez linię programu po wierszu lub wybrać **kontynuuj** (**F5**), aby uruchomić go do zakończenia (lub następnego punktu przerwania).

Aby przejść głębiej, zobacz [Debugowanie](debugging-r-in-visual-studio.md) i [Eksplorator zmiennych](variable-explorer.md).

## <a name="next-steps"></a>Następne kroki

W tym instruktażu poznaliście podstawy projektów języka R, korzystając z interaktywnego okna, edycji kodu i debugowania w programie Visual Studio. Aby kontynuować eksplorowanie większej liczby możliwości, zobacz następujące artykuły, a także artykuły wyświetlane w spisie treści:

- [Przykładowe projekty](getting-started-samples.md)
- [Edytowanie kodu](editing-r-code-in-visual-studio.md)
- [Debugging](debugging-r-in-visual-studio.md)
- [Obszary robocze](r-workspaces-in-visual-studio.md)
- [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md)
