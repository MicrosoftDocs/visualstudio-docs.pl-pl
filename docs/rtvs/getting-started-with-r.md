---
title: Samouczek z wprowadzeniem do języka R
description: Przewodnik po użyciu języka R w programie Visual Studio, w tym tworzenie projektu, okno interaktywne, edytowanie kodu i debugowanie.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8be766e078a04d713ed69aa0b9cc464433dcb73d
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761397"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Wprowadzenie do R Tools for Visual Studio

Po zainstalowaniu programu R Tools for Visual Studio (zobacz temat [Instalacja](installing-r-tools-for-visual-studio.md)) można szybko uzyskać dostęp do tych narzędzi.

## <a name="create-an-r-project"></a>Tworzenie projektu R

1. Otwórz program Visual Studio.
1. Wybierz pozycję **plik**  >  **Nowy**  >  **projekt** (**Ctrl** + **SHIFT** + **N**)
1. Wybierz pozycję "projekt r" z sekcji **Szablony**  >  **R**, Nadaj projektowi nazwę i lokalizację, a następnie wybierz **przycisk OK**:

   ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w program VS2017)](media/getting-started-01-new-project.png)

1. Po utworzeniu projektu zostaną wyświetlone następujące okna:

    - Po prawej stronie jest program Visual Studio Eksplorator rozwiązań, w którym Twój projekt jest widoczny w ramach *rozwiązania* zawierającego. (Rozwiązania mogą zawierać dowolną liczbę projektów różnych typów; Aby uzyskać szczegółowe informacje, zobacz [projekty](r-projects-in-visual-studio.md) .
    - W lewym górnym rogu znajduje się nowy plik języka R ( `script.R` ), w którym można edytować kod źródłowy ze wszystkimi funkcjami edycji programu Visual Studio.
    - W lewym dolnym rogu znajduje się okno **R Interactive** , w którym można interaktywnie opracowywać i testować kod.

> [!Note]
> Można użyć okna **R Interactive** bez otwierania żadnych projektów, a nawet w przypadku załadowania innego typu projektu. Po prostu wybierz pozycję **R Tools**  >  **Windows**  >  **R Interactive** w dowolnym momencie.

## <a name="explore-the-interactive-window-and-intellisense"></a>Eksploruj okno interaktywne i funkcję IntelliSense

1. Sprawdź, czy okno interaktywne działa, wpisując w `3 + 4` , a następnie **Enter** , aby zobaczyć wynik:

    ![Okno R Interactive w programie Visual Studio 2017 (program VS2017)](media/getting-started-02-interactive1.png)

1. Wprowadź nieco bardziej skomplikowany element, `ds <- c(1.5, 6.7, 8.9) * 1:12` a następnie wprowadź, `ds` Aby zobaczyć wynik:

    ![Dodatkowy przykład interaktywny dla języka R w programie Visual Studio](media/getting-started-03-interactive2.png)

1. Wpisz, `mean(ds)` ale pamiętaj, że zaraz po wpisaniu `m` lub `me` , funkcja IntelliSense programu Visual Studio udostępnia opcje Autouzupełniania. Po wybraniu na liście żądanego zakończenia naciśnij klawisz **Tab** , aby go wstawić. Zaznaczenie można zmienić za pomocą klawiszy strzałek lub myszy.

    ![Technologia IntelliSense pojawia się podczas wprowadzania kodu](media/getting-started-04-intellisense1.png)

1. Po zakończeniu `mean` Wpisz nawias otwierający `(` i zwróć uwagę na to, w jaki sposób technologia IntelliSense oferuje wbudowaną pomoc dla funkcji:

    ![Technologia IntelliSense pokazująca pomoc dla funkcji](media/getting-started-05-intellisense2.png)

1. Wypełnij wiersz `mean(ds)` i naciśnij klawisz ENTER, aby zobaczyć wynik ( `[1] 39.51667` ).

1. Okno interaktywne jest zintegrowane z pomocą, więc wprowadzenie `?mean` wyświetla pomoc dla tej funkcji w oknie **Pomoc dla języka R** w programie Visual Studio. Aby uzyskać szczegółowe informacje, zobacz [Pomoc w R Tools for Visual Studio](getting-started-help.md).

    ![Okno Pomoc dla języka R w programie Visual Studio](media/getting-started-06-help.png)

1. Niektóre polecenia, takie jak `plot(1:100)` , otwierają nowe okno w programie Visual Studio, gdy dane wyjściowe nie mogą być wyświetlane bezpośrednio w oknie interaktywnym:

    ![Zrzut ekranu przedstawiający okno programu Visual Studio R Graph zawierające dane wyjściowe wykresu funkcji grafu (1:100).](media/getting-started-07-plot-window.png)

Okno interaktywne pozwala także przeglądać historię, ładować i zapisywać obszary robocze, dołączać do debugera oraz korzystać z plików kodu źródłowego zamiast używać kopiowania i wklejania. Aby uzyskać szczegółowe informacje [, zobacz Praca z oknem R Interactive](interactive-repl-for-r-in-visual-studio.md) .

## <a name="experience-code-editing-features"></a>Funkcje edytowania kodu środowiska

Praca z oknem Interactive pokazuje podstawowe funkcje edycji, takie jak IntelliSense, które również działają w edytorze kodu. Jeśli wprowadzisz ten sam kod jak wcześniej, zobaczysz te same polecenia autouzupełniania i IntelliSense, ale nie dane wyjściowe.

Pisanie kodu w *. Plik R* pozwala zobaczyć cały kod jednocześnie i ułatwia wprowadzanie małych zmian, a następnie szybkie wyświetlanie wyników przez uruchomienie kodu w oknie interaktywnym. Możesz również mieć dowolną liczbę plików w projekcie. Gdy kod znajduje się w pliku, można również uruchomić go krok po kroku w debugerze (opisany w dalszej części tego artykułu). Te funkcje są przydatne, gdy tworzysz algorytmy obliczeniowe i piszesz kod w celu manipulowania jednym lub wieloma zestawami danych, zwłaszcza gdy chcesz przeanalizować wszystkie pośrednie wyniki.

Na przykład następujące kroki tworzą mały kod, aby poznać [centralny limit theorem](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Ten przykład jest dostosowywany z *Cookbook R* przez Paul Teetor).

1. W `script.R` Edytorze wprowadź następujący kod:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Aby szybko zobaczyć wyniki, zaznacz cały kod (**Ctrl** + **A**), a następnie naciśnij klawisz **Ctrl** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz pozycję **wykonaj w trybie interaktywnym**. Cały wybrany kod jest uruchamiany w oknie interaktywnym, tak jak w przypadku jego wpisania bezpośrednio, pokazując wynik w oknie wykresu:

    ![Zrzut ekranu przedstawiający okno wykresu programu Visual Studio R przedstawiające wykres gęstości populacji.](media/getting-started-08-plot1.png)

1. W przypadku pojedynczego wiersza po prostu naciśnij klawisz **Ctrl** + **Enter** w dowolnym momencie, aby uruchomić ten wiersz w oknie interaktywnym.

> [!Tip]
> Zapoznaj się z wzorcem wprowadzania zmian i naciśnięciem klawisza **Ctrl** +  (lub Zaznacz wszystko przy użyciu **kombinacji Ctrl** + **a** i naciśnij klawisz **Ctrl** + **Enter**), aby szybko uruchomić kod. Wykonanie tej czynności jest znacznie bardziej wydajne niż używanie myszy na potrzeby tych samych operacji.
>
> Ponadto możesz przeciągnąć i upuścić okno kreolenia poza ramką programu Visual Studio i umieścić je w dowolnym miejscu na ekranie. Następnie można zmienić rozmiar okna wykresu na żądany wymiar, a następnie zapisać go do obrazu lub pliku PDF.

1. Dodaj kilka więcej wierszy kodu, aby dołączyć drugi wykres:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Naciśnij klawisze **Ctrl** + **a** i **Ctrl** +  ponownie, aby uruchomić kod, generując następujący wynik:

    ![Zaktualizowany podwójny wykres w programie Visual Studio](media/getting-started-09-plot2.png)

1. Problem polega na tym, że pierwszy wykres określa skalę pionową, więc drugie Kreślenie (z `lines` ) nie mieści się. Aby rozwiązać ten problem, należy ustawić `ylim` parametr w `plot` wywołaniu, ale tak aby prawidłowo musiałmy dodać kod, aby obliczyć maksymalną wartość pionową. Wykonanie tego wiersza w oknie interaktywnym jest niewygodne, ponieważ musimy zmienić rozmieszczenie kodu do użycia `samp.means` przed wywołaniem `plot` . Chociaż w pliku kodu można łatwo wprowadzić odpowiednie zmiany:

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

1. **Ctrl** + **A** i **naciśnij klawisz** + **Enter** , aby zobaczyć wynik:

    ![Zaktualizowano podwójny wykres w programie Visual Studio, prawidłowo skalowany](media/getting-started-10-plot3.png)

Można to zrobić w edytorze. Aby uzyskać szczegółowe informacje, zobacz [Edycja kodu R](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md)i [fragmenty kodu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Debugowanie kodu

Jedną z najważniejszych zalet programu Visual Studio jest interfejs użytkownika debugowania. RTVS kompiluje się w oparciu o tę silną podstawę i dodaje innowacyjny interfejs użytkownika, taki jak [Eksplorator zmiennych](variable-explorer.md). Po prostu Przyjrzyjmy się najpierw debugowaniu.

1. Aby rozpocząć, zresetuj bieżący obszar roboczy, aby wyczyścić wszystkie zrobione dotąd operacje przy użyciu   >    >  polecenia menu **resetowania** sesji języka R. Domyślnie wszystkie czynności wykonywane w oknie interaktywnym naliczane są do bieżącej sesji, która jest również używana przez debuger. Przez zresetowanie sesji, należy się upewnić, że sesja debugowania rozpoczyna się od braku istniejących danych. Polecenie **Reset** nie ma jednak wpływu na *skrypt. Plik źródłowy języka R* , ponieważ jest zarządzany i zapisywany poza obszarem roboczym.

1. Za pomocą *skryptu. Plik R* utworzony w poprzedniej sekcji Ustaw punkt przerwania w wierszu, który rozpoczyna się od `pop <-` przez umieszczenie karetki w tym wierszu, a następnie naciśnięcie klawisza **F9** lub wybranie polecenia **Debuguj**  >  **Przełącz punkt przerwania** . Alternatywnie możesz kliknąć na lewym marginesie (lub marginesie) dla tego wiersza, gdzie pojawia się czerwona kropka punktu przerwania:

    ![Ustawianie punktu przerwania w edytorze](media/getting-started-11-debug1.png)

1. Uruchom Debuger z kodem w *skrypcie. R* przez wybranie przycisku **źródłowy plik startowy** na pasku narzędzi, wybranie   >  pozycji menu **plik startowy źródła** debugowania lub naciśnięcie klawisza **F5**. Program Visual Studio przechodzi w tryb debugowania i zaczyna działać w kodzie. W wierszu, w którym ustawiany jest punkt przerwania:

    ![Zatrzymywanie w punkcie przerwania w debugerze programu Visual Studio](media/getting-started-12-debug2.png)

1. Podczas debugowania program Visual Studio umożliwia przechodzenie krok po kroku przez wiersz kodu. Możesz również przejść do sekcji Functions, Przekrocz je lub przekroczyć kontekst wywołujący. Te możliwości, wraz z innymi, można znaleźć w menu **debugowanie** , menu kontekstowym prawym przyciskiem myszy w edytorze oraz na pasku narzędzi debugowania:

    ![Debuguj pasek narzędzi w programie Visual Studio](media/getting-started-13-debug3.png)

1. Po zatrzymaniu w punkcie przerwania można przeanalizować wartości zmiennych. Znajdź okno **autostarts** w programie Visual Studio i wybierz kartę wzdłuż dołu o nazwie **locale**. W oknie **Ustawienia lokalne** są wyświetlane zmienne lokalne w bieżącym punkcie programu. Jeśli zatrzymasz się w ustawionym wcześniej punkcie przerwania, zobaczysz, że `pop` zmienna nie jest jeszcze zdefiniowana. Teraz użyj polecenia **Debuguj**  >  **krok po kroku** (**F10**) i zobaczysz wartość `pop` wyświetlaną:

    ![Okno zmiennych lokalnych w programie Visual Studio](media/getting-started-14-debug4.png)

1. Aby przejrzeć zmienne w różnych zakresach, w tym zakres globalny i zakresy pakietów, użyj [Eksplorator zmiennych](variable-explorer.md). Eksplorator zmiennych daje również możliwość przełączenia się do widoku tabelarycznego z sortowaniem kolumn i eksportowanie danych do pliku CSV.

    ![Rozwinięty widok Eksplorator zmiennych](media/variable-explorer-expanded-results.png)

1. Możesz kontynuować krok po kroku wiersz programu lub przycisk **Kontynuuj** (**F5**), aby uruchomić go w celu ukończenia (lub następnego punktu przerwania).

Aby dowiedzieć się więcej, zobacz [debugowanie](debugging-r-in-visual-studio.md) i [Eksplorator zmiennych](variable-explorer.md).

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono podstawowe zagadnienia dotyczące projektów języka R, przy użyciu okna interaktywnego, edytowania kodu i debugowania w programie Visual Studio. Aby kontynuować Eksplorowanie więcej możliwości, zobacz następujące artykuły i artykuły widoczne w spisie treści:

- [Przykładowe projekty](getting-started-samples.md)
- [Edytowanie kodu](editing-r-code-in-visual-studio.md)
- [Debugowanie](debugging-r-in-visual-studio.md)
- [Obszary robocze](r-workspaces-in-visual-studio.md)
- [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md)
