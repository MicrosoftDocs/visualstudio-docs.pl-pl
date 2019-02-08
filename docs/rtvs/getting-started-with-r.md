---
title: Wprowadzenie do samouczka języka R
description: Przewodnik po przy użyciu języka R w programie Visual Studio, w tym oknie interaktywnym, tworzenia projektu kodu, edytowanie i debugowanie.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d3ef293b4e25f85cd901c42382158bdd75742e26
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936424"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Rozpocznij pracę z narzędziami języka R dla programu Visual Studio

Po utworzeniu R Tools for Visual Studio (RTVS) zainstalowane (zobacz [instalacji](installing-r-tools-for-visual-studio.md)), możesz szybko uzyskać smak środowisko, które zapewniają tych narzędzi.

## <a name="create-an-r-project"></a>Tworzenie projektu języka R

1. Uruchom program Visual Studio.
1. Wybierz **pliku** > **nowe** > **projektu** (**Ctrl**+**Shift** + **N**)
1. Wybierz pozycję "Projekt R" w obszarze **szablony** > **R**, należy nadać projektowi nazwę i lokalizację i wybierz **OK**:

   ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w programie VS2017)](media/getting-started-01-new-project.png)

1. Po utworzeniu projektu zostaną wyświetlone następujące systemu windows:

    - Po prawej stronie jest Visual Studio Eksplorator rozwiązań tam, gdzie zobaczysz projektu w nadrzędnym *rozwiązania*. (Rozwiązania może zawierać dowolną liczbę projektów o różnych typach; zobacz [projektów](r-projects-in-visual-studio.md) Aby uzyskać szczegółowe informacje.
    - W lewym górnym rogu jest nowy plik języka R (`script.R`) funkcje umożliwiające edytowanie kodu źródłowego za pomocą całego programu Visual Studio jego edycji.
    - W lewym dolnym rogu **interaktywne R** okna, w którym możesz interaktywnie opracowywać i testować kod.

> [!Note]
> Możesz użyć **interaktywne R** okna bez jakiegokolwiek projektu, Otwórz, a nawet, gdy typ inny projekt jest ładowany. Po prostu wybierz opcję **R Tools** > **Windows** > **interaktywne R** w dowolnym momencie.

## <a name="explore-the-interactive-window-and-intellisense"></a>Zapoznaj się z oknie interaktywnym i technologii IntelliSense

1. Test, który działa, wpisując w oknie interaktywnym `3 + 4` i następnie **Enter** można przejrzeć wyniki:

    ![Okno interaktywne R w programie Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Wprowadź coś bardziej skomplikowane nieco, `ds <- c(1.5, 6.7, 8.9) * 1:12`, a następnie wprowadź `ds` można przejrzeć wyniki:

    ![Dodatkowe przykład interaktywne dla języka R w programie Visual Studio](media/getting-started-03-interactive2.png)

1. Wpisz `mean(ds)` , ale Zwróć uwagę, że jak najszybciej po wpisaniu `m` lub `me`, funkcji IntelliSense Visual Studio udostępnia opcje automatycznego uzupełniania. Po wybraniu na liście uzupełniania, należy nacisnąć klawisz **kartę** do wstawienia; możesz zmienić wybór za pomocą klawiszy strzałek lub myszy.

    ![Funkcja IntelliSense, pojawiają się podczas wprowadzania kodu](media/getting-started-04-intellisense1.png)

1. Po zakończeniu `mean`, wpisz nawias otwierający `(` i zwróć uwagę, jak technologia IntelliSense umożliwia wbudowanej pomocy dla funkcji:

    ![Wyświetlanie pomocy dla funkcji IntelliSense](media/getting-started-05-intellisense2.png)

1. Wykonaj wiersz `mean(ds)` i naciśnij klawisz Enter, aby wyświetlić wynik (`[1] 39.51667`).

1. Okno interaktywne jest zintegrowana z usługą pomocy, więc wprowadzanie `?mean` Wyświetla Pomoc dotyczącą tej funkcji w **pomocy R** okna w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [ułatwić R Tools for Visual Studio](getting-started-help.md).

    ![Pomoc języka R okna w programie Visual Studio](media/getting-started-06-help.png)

1. Niektóre polecenia takie jak `plot(1:100)`, Otwórz nowe okno w programie Visual Studio, gdy nie można wyświetlić dane wyjściowe bezpośrednio w oknie interaktywnym:

    ![Wyświetl wykres w programie Visual Studio](media/getting-started-07-plot-window.png)

Okno interaktywne umożliwia także Przejrzyj historię, ładowania i zapisywania obszarów roboczych, dołączenia do debugera i wchodzić w interakcje z plikami kodu źródłowego, zamiast kopiowania i wklejania. Zobacz [pracę w oknie interaktywnym r.](interactive-repl-for-r-in-visual-studio.md) Aby uzyskać szczegółowe informacje.

## <a name="experience-code-editing-features"></a>Funkcje edytowania kodu środowiska

Krótko z okna interaktywnego Praca pokazuje podstawowych funkcji edycji takie jak technologia IntelliSense, które również działają w edytorze kodu. Po wprowadzeniu tego samego kodu, jak wcześniej, zostanie wyświetlony ten sam automatycznego uzupełniania i monity o technologii IntelliSense, ale nie dane wyjściowe.

Pisanie kodu w *. R* pliku pozwala od razu zobaczyć cały kod i ułatwia dokonywać niewielkich zmian, a następnie szybko wyświetlić wynik, uruchamiając kod w oknie interaktywnym. Może również mieć tyle plików w projekcie. Gdy kod jest w pliku, można również uruchomić go krok w debugerze (zostało to omówione w dalszej części tego artykułu). Te możliwości są przydatne podczas tworzenia algorytmy obliczeniową i pisanie kodu do manipulowania jeden lub więcej zestawów danych, szczególnie w przypadku, gdy chcesz sprawdzić wszystkie wyniki pośrednie.

Na przykład poniższe kroki umożliwiają utworzenie niewielkiej ilości kodu, aby zapoznać się z [centralnej teorii Limit](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (W tym przykładzie są zaczerpnięte z *Podręcznik języka R* , Paul Teetor.)

1. W `script.R` edytora, wprowadź następujący kod:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Aby szybko wyświetlić wyniki, wybierz cały kod (**Ctrl**+**A**), naciśnij klawisz **Ctrl**+**Enter** lub Kliknij prawym przyciskiem myszy i wybierz **wykonaj w trybie interaktywnym**. Wszystkie wybrane kod jest uruchamiany w oknie interaktywnym, tak, jakby został wpisany bezpośrednio, przedstawiający wyniki w oknie wykresu:

    ![Wyświetl wykres w programie Visual Studio](media/getting-started-08-plot1.png)

1. Dla pojedynczego wiersza, zamiast tego nacisnąć klawisze **Ctrl**+**Enter** w dowolnym momencie, aby uruchomić ten wiersz w oknie interaktywnym.

> [!Tip]
> Dowiedz się wzorzec wprowadzanie zmian i naciskając klawisz **Ctrl**+**Enter** (lub wybierz wszystko z **Ctrl**+**A** , a następnie naciskając klawisz **Ctrl**+**Enter**) Aby szybko uruchomić kod. Ten sposób jest znacznie bardziej efektywne niż do tej samej operacji przy użyciu myszy.
>
> Ponadto można przeciągnij i upuść okna wykres poza ramek programu Visual Studio i umieść go, zawsze wtedy, gdy inne chcesz, aby na ekranie. Następnie można zmienić rozmiar okna diagram wymiarów i zapisz go do obrazu lub pliku PDF.

1. Dodaj kilku więcej wierszy kodu, aby uwzględnić drugi wykres:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Naciśnij klawisz **Ctrl**+**A** i **Ctrl**+**Enter** ponownie, aby uruchomić kod, tworzyć następujące wyniki:

    ![Zaktualizowany wykres podwójną w programie Visual Studio](media/getting-started-09-plot2.png)

1. Problem polega na pierwszy wykres określa skali pionowej, więc drugi wykresu (przy użyciu `lines`) nie pasuje. Aby rozwiązać ten problem, należy ustawić `ylim` parametru `plot` wywołań, ale działają tak, aby prawidłowo musimy dodać kod do obliczenia maksymalnej wartości pionowy. Wykonując ten wiersz po wierszu w oknie interaktywnym jest wygodne, ponieważ należy do zmiany rozmieszczenia kod, aby użyć `samp.means` przed wywołaniem `plot`. W pliku kodu jednak firma Microsoft można łatwo wprowadzić odpowiednie zmiany:

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

1. **CTRL**+**A** i **Ctrl**+**Enter** ponownie, aby zobaczyć wynik:

    ![Zaktualizowany wykres podwójną w programie Visual Studio, prawidłowo skalowany](media/getting-started-10-plot3.png)

Istnieje więcej, możesz zrobić w edytorze. Aby uzyskać więcej informacji, zobacz [kod R Edytuj](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md), i [fragmenty kodu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Debugowanie kodu

Jedną z kluczowych zalet programu Visual Studio jest jej debugowania interfejsu użytkownika. RTVS opiera się na takim fundamencie silnych i dodaje innowacyjne interfejsu użytkownika, takie jak [narzędzie Variable Explorer](variable-explorer.md). W tym miejscu po prostu Przyjrzyjmy Pierwsze spojrzenie na profilowanie.

1. Aby rozpocząć, resetowanie bieżącego obszaru roboczego, aby wyczyścić wszystkie elementy zostały wykonane do tej pory przy użyciu **R Tools** > **sesji** > **resetowania** polecenia menu. Domyślnie wszystko, co można zrobić w oknie interaktywnym przypadającą na bieżącej sesji, który następnie jest również używany przez debuger. Resetowanie sesji, gwarantuje, że sesji debugowania zaczyna się od żadnych istniejących danych. **Resetowania** polecenia, jednak nie ma wpływu na Twoje *skryptu. R* źródła pliku, ponieważ ma, zarządzane i zapisany poza obszar roboczy.

1. Za pomocą *skryptu. R* plik utworzony w poprzedniej sekcji, ustaw punkt przerwania w wierszu, który rozpoczyna się od `pop <-` umieszczenie karetkę w danym wierszu, a następnie naciskając klawisz **F9**, lub wybierając **debugowania**  >  **Przełącz punkt przerwania** polecenia menu. Alternatywnie, po prostu kliknij w lewym marginesie (lub trasę) dla tego wiersza, w którym kropka czerwony punktu przerwania pojawia się:

    ![Ustawienie punktu przerwania w edytorze](media/getting-started-11-debug1.png)

1. Uruchom debuger kodu z *skryptu. R* wybierając **źródłowy plik startowy** przycisk na pasku narzędzi, wybierając **debugowania** > **źródłowy plik startowy** elementów menu lub naciskając **F5**. Visual Studio przechodzi do trybu debugowania i uruchamiania kodu. Go zatrzymuje się jednak, w wierszu, gdzie ustawić punkt przerwania:

    ![Zatrzymywanie punkt przerwania w debugerze programu Visual Studio](media/getting-started-12-debug2.png)

1. Podczas debugowania, Visual Studio pozwala krokowo kodu wiersz po wierszu. Można również wkroczenia do funkcji, Przekrocz nad nimi, lub wychodzenie z nich do wywoływania kontekstu. Te możliwości, wraz z innymi, można znaleźć na **debugowania** menu, kliknij prawym przyciskiem myszy menu kontekstowego w edytorze i na pasku narzędzi debugowania:

    ![Pasek narzędzi w programie Visual Studio debugowania](media/getting-started-13-debug3.png)

1. Po zatrzymaniu w punkcie przerwania, można sprawdzić wartości zmiennych. Znajdź **Autos** okna w programie Visual Studio i wybierz karty u dołu o nazwie **lokalne**. **Lokalne** okno pokazuje zmiennych lokalnych w bieżącym punkcie w programie. Jeśli użytkownik jest zatrzymana na wcześniej ustawić punkt przerwania, zobaczysz, że `pop` zmienna nie jest jeszcze zdefiniowana. Teraz za pomocą **debugowania** > **Step Over** polecenia (**F10**), i sprawdź wartość `pop` wyświetlane:

    ![Okno zmiennych lokalnych w programie Visual Studio](media/getting-started-14-debug4.png)

1. Aby zbadać zmienne w różnych zakresach, w tym zakresie globalnym i zakresy pakietu, należy użyć [narzędzie Variable Explorer](variable-explorer.md). Narzędzie Variable Explorer oferuje również możliwość przełączać do widoku tabelarycznego z kolumnami sortowania i eksportowanie danych do pliku CSV.

    ![Rozwinięty widok Eksplorator zmiennych](media/variable-explorer-expanded-results.png)

1. Możesz kontynuować przechodzenie krok po kroku, za pośrednictwem programu wiersz po wierszu, lub wybierz opcję **Kontynuuj** (**F5**) do jej uruchomienia do ukończenia (lub następnego punktu przerwania).

Aby bardziej szczegółowo omawiają, zobacz [debugowanie](debugging-r-in-visual-studio.md) i [narzędzie Variable Explorer](variable-explorer.md).

## <a name="next-steps"></a>Następne kroki

W tym przewodniku wyjaśniono podstawowe informacje dotyczące projekty języka R, użycie okna interaktywnego, code edytowanie i debugowanie w programie Visual Studio. Aby kontynuować Eksplorowanie więcej możliwości, zobacz następujące artykuły oraz artykułów ukazał spisu treści:

- [Przykładowe projekty](getting-started-samples.md)
- [Edytowanie kodu](editing-r-code-in-visual-studio.md)
- [Debugowanie](debugging-r-in-visual-studio.md)
- [Obszary robocze](r-workspaces-in-visual-studio.md)
- [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md)
