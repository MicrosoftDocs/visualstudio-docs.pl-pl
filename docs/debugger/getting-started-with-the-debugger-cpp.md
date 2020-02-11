---
title: 'Samouczek: debugowanie C++ kodu'
description: Dowiedz się, jak uruchomić debuger programu Visual Studio, Przechodź przez kod i sprawdzić dane.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b1a031a6c4e4e823a1fcc12aba228750aee27e
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091811"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: Dowiedz się debugować kod C++ przy użyciu programu Visual Studio

W tym artykule przedstawiono funkcje debugera programu Visual Studio w przewodnik krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). Gdy *debugujesz aplikację*, zazwyczaj oznacza to, że aplikacja jest uruchamiana z dołączonym debugerem. Gdy to zrobisz, debuger zapewnia wiele sposobów, aby zobaczyć, co kod robi podczas jego uruchamiania. Można przejść przez kod i przyjrzyj się wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmienić wartości, można zbadać ścieżki wykonywania kodu, czy gałąź kodu nie jest uruchomiona, i tak dalej. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przejściem do tego artykułu warto przeczytać [debugowanie dla bezwzględnych początkujących](../debugger/debugging-absolute-beginners.md) .

Mimo że aplikacja demonstracyjna C++to, większość funkcji ma zastosowanie do C#, Visual Basic, F#, Python, JavaScript i innych języków obsługiwanych przez program Visual Studio (F# nie obsługuje funkcji Edit-and-Continue. F#i język JavaScript nie obsługuje okna **autostarts** ). Zrzuty ekranu znajdują się w C++temacie.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i identyfikować punkty przerwania.
> * Dowiedz się więcej poleceń, aby przejść przez kod w debugerze
> * Sprawdzanie zmiennych w oknach debugera i porady dotyczące danych
> * Sprawdź stos wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany program Visual Studio 2019 i **programowanie C++ dla komputerów stacjonarnych** .

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany program Visual Studio 2017 i **programowanie C++ dla komputerów stacjonarnych** .

::: moniker-end

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Uruchamia Instalatora programu Visual Studio. Wybierz pozycję **programowanie C++ dla komputerów stacjonarnych** , a następnie wybierz polecenie **Modyfikuj**.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji C++ konsolowej. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Wizualizacja C++**  , a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**. Następnie nadaj nazwę projekt *Get-Started-Debug*.

     Jeśli szablon projektu **aplikacji konsolowej** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

4. Kliknij przycisk **OK**.

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **C++** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie C++ szablonu dla aplikacji konsolowej](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Jeśli szablon **aplikacji konsolowej** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz pozycję **Programowanie dla komputerów z C++**  obciążeniem.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź w polu **Nazwa projektu** polecenie *Get-Started-Debug* . Następnie wybierz pozycję **Utwórz**.

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *Get-Started-Debugging. cpp*Zastąp cały kod domyślny następującym kodem:

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

     **F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale teraz nie robimy żadnych specjalnych, aby przeanalizować kod. Dlatego właśnie ładowania aplikacji, a zostaną wyświetlone dane wyjściowe konsoli.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     W tym samouczku utworzymy Przyjrzyj się bliżej aplikacji przy użyciu debugera i pobrać spojrzenie na debugera funkcji.

2. Zatrzymaj debuger, naciskając czerwony przycisk Zatrzymaj ![debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") (**SHIFT** + **F5**).

3. W oknie konsoli naciśnij klawisz i **wprowadź** , aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomić debuger

1. W pętli `for` funkcji `main` Ustaw punkt przerwania, klikając lewy margines w następującym wierszu kodu:

    `name += letters[i];`

    W miejscu ustawionym na ![punkt przerwania pojawia się](../debugger/media/dbg-breakpoint.png "Punkt przerwania") czerwony okrąg.

    Punkty przerwania są jedną z najważniejszych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

2. Naciśnij klawisz **F5** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie"), uruchomienie aplikacji, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawiono punkt przerwania.

    ![Ustaw i Traf punkt przerwania](../debugger/media/get-started-set-breakpoint-cpp.png)

    Żółta strzałka reprezentuje instrukcji, w której debuger wstrzymany, również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie jeszcze wykonane).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchamia debuger i kończy się przy pierwszym punkcie przerwania. W przeciwnym razie **F5** kontynuuje działanie aplikacji do następnego punktu przerwania.

    Punkty przerwania są to przydatne, gdy wiadomo, wiersz kodu lub sekcji kodu, który chcesz zbadać szczegółowo. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Przechodzenie do kodu w debugerze, przy użyciu poleceń krokowych

Przede wszystkim, używamy skróty klawiaturowe w tym miejscu, ponieważ jest to dobry sposób, aby uzyskać szybkie na wykonywanie aplikacji w debugerze (równoważne polecenia takie jak menu poleceń są wyświetlane w nawiasach).

1. Gdy jest wstrzymana w pętli `for` w metodzie `main`, naciśnij klawisz **F11** (lub wybierz polecenie **Debuguj > Wkrocz**) dwa razy, aby przejść do wywołania metody `SendMessage`.

     Po dwukrotnym naciśnięciu klawisza **F11** należy mieć następujący wiersz kodu:

     `SendMessage(name, a[i]);`

1. Naciśnij klawisz **F11** jeszcze raz, aby przejść do metody `SendMessage`.

     Żółty wskaźnik jest zaawansowany do metody `SendMessage`.

     ![Użyj klawisza F11, aby przejść do kodu](../debugger/media/get-started-f11-cpp.png "Wkrocz do kroku")

     F11 to **krok do** polecenia i postępuje z jedną instrukcją wykonywania aplikacji w danym momencie. F11 jest dobrym sposobem na zbadanie przepływ wykonania w najbardziej szczegółowy. (Aby szybciej przejść przez kod, pokazujemy inne opcje.) Domyślnie debuger pomija kod niebędący użytkownikiem (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../debugger/just-my-code.md)).

     Załóżmy, że skończysz badanie metody `SendMessage` i chcesz uzyskać dostęp do metody, ale pozostać w debugerze. Można to zrobić przy użyciu polecenia **krok po kroku** .

1. Naciśnij klawisz **Shift** + **F11** (lub **Debuguj > krok**).

     To polecenie wznawia wykonywanie aplikacji (i zwiększa debuger) do momentu, gdy bieżąca metoda lub funkcja zwróci wynik.

     Należy wrócić do pętli `for` w metodzie `main`, wstrzymane w wywołaniu metody `SendMessage`.

1. Naciśnij klawisz **F11** kilka razy, dopóki nie powrócisz do wywołania metody `SendMessage`.

1. Po wstrzymaniu wywołania metody naciśnij klawisz **F10** (lub wybierz polecenie **Debuguj > krok więcej**).

     ![Użyj klawisza F10, aby przekroczyć kod](../debugger/media/get-started-step-over-cpp.png "F10 krok po kroku")

     Zauważ, że debuger nie przekroczy metody `SendMessage`. **F10** przesuwa debuger bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod nadal jest wykonywany). Naciskając klawisz **F10** w wywołaniu metody `SendMessage` (zamiast **F11**), pominięto kod implementacji dla `SendMessage` (co może nie interesuje Cię teraz). Aby uzyskać więcej informacji na temat różnych sposobów poruszania się po kodzie, zobacz [nawigowanie po kodzie w debugerze](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Przechodzenie do kodu przy użyciu polecenia Uruchom do kliknięcia

1. Naciśnij klawisz **F5** , aby przejść do punktu przerwania.

1. W edytorze kodu przewiń w dół i umieść kursor nad funkcją `std::wcout` w metodzie `SendMessage` do momentu, gdy zielony przycisk Uruchom ![do kliknięcia zostanie wyświetlony po](../debugger/media/dbg-tour-run-to-click.png "RunToClick") lewej stronie. Etykietka narzędzia dla przycisku pokazuje "uruchom wykonywanie do tego miejsca".

     ![Korzystanie z funkcji uruchamiania do kliknięcia](../debugger/media/get-started-run-to-click-cpp.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom do kliknięcia** jest nowy w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. (Jeśli nie widzisz przycisku Zielona strzałka, użyj klawisza **F11** w tym przykładzie zamiast, aby przejść do odpowiedniego miejsca w debugerze).

2. Kliknij przycisk **Uruchom, aby kliknąć** polecenie ![Uruchom, aby kliknąć](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger przechodzi do funkcji `std::wcout`.

    Za pomocą tego przycisku jest podobna do ustawienia tymczasowy punkt przerwania. **Uruchamianie do kliknięcia** jest przydatne do szybkiego szybszego wprowadzania informacji w widocznym regionie kodu aplikacji (można kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybko Uruchom ponownie swoją aplikację

Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**).

Po naciśnięciu przycisku **Uruchom ponownie**program zapisze czas w przeciwieństwie do zatrzymywania aplikacji i ponownego uruchomienia debugera. Debuger wstrzymuje na pierwszy punkt przerwania zostanie osiągnięty przez wykonywanie kodu.

Debuger zatrzyma się ponownie w punkcie przerwania, który został wcześniej ustawiony wewnątrz pętli `for`.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych z poradami do danych

Funkcje, które pozwalają na sprawdzanie zmiennych są jednymi z najbardziej przydatnych funkcjach debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz sprawdzić, czy zmienne są przechowywane wartości, których można oczekiwać, aby użytkownicy posiadali w danym momencie.

1. Gdy jest wstrzymana w instrukcji `name += letters[i]`, umieść wskaźnik myszy na zmiennej `letters` i zobaczysz jej wartość domyślną, `size={10}`.

1. Rozwiń zmienną `letters`, aby wyświetlić jej właściwości, które obejmują wszystkie elementy, które zawiera zmienna.

1. Następnie umieść wskaźnik myszy nad zmienną `name` i zobaczysz jej bieżącą wartość jako pusty ciąg.

1. Naciśnij klawisz **F5** (lub **Debuguj** > **Kontynuuj**) kilka razy, aby wielokrotnie powtarzać kilka razy przez pętlę `for`, zatrzymując ponownie w punkcie przerwania i umieszczając wskaźnik myszy na zmiennej `name` za każdym razem, aby sprawdzić jej wartość.

     ![Wyświetlanie etykietki danych](../debugger/media/get-started-data-tip-cpp.png "Wyświetlanie etykietki danych")

     Wartość zmiennej zmienia się z każdą iteracją `for` pętli, wyświetlając wartości `f`, następnie `fr`, a następnie `fre`i tak dalej.

     Często podczas debugowania, chcesz, aby szybko sprawdzić wartości zmiennych, aby zobaczyć, czy będą one przechowywane wartości, których oczekujesz, aby przechowywać, właściwości i porady dotyczące danych są dobrym sposobem, aby to zrobić.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Zapoznaj się z oknem **Autokorekty** u dołu edytora kodu.

    Jeśli jest zamknięte, otwórz je podczas wstrzymania w debugerze, wybierając pozycję **debuguj** > **Windows** > **autostarts**.

    W oknie **Autokorekty** widoczne są zmienne i ich bieżąca wartość. W oknie **samochody** są wyświetlane wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (Sprawdź dokumentację zachowania specyficzną dla języka).

1. Następnie zapoznaj się z oknem **Locals (ustawienia regionalne** ) na karcie obok okna **Autokorekty** .

1. Rozwiń zmienną `letters`, aby wyświetlić elementy, które zawiera.

     ![Sprawdź zmienne w oknie zmiennych lokalnych](../debugger/media/get-started-locals-window-cpp.png "Okno zmiennych lokalnych")

    W oknie **Ustawienia lokalne** są wyświetlane zmienne, które znajdują się w bieżącym [zakresie](https://www.wikipedia.org/wiki/Scope_(computer_science)), czyli bieżącym kontekście wykonania.

## <a name="set-a-watch"></a>Ustawianie wyrażenia kontrolnego

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy zmienną `name` i wybierz polecenie **Dodaj czujkę**.

    Zostanie otwarte okno **czujki** w dolnej części edytora kodu. Możesz użyć okna **czujki** , aby określić zmienną (lub wyrażenie), dla którego chcesz zachować czujkę.

    Teraz masz ustawiony czujkę na zmiennej `name` i zobaczysz jej zmianę wartości podczas przechodzenia przez debuger. W przeciwieństwie do innych zmiennych okien, w oknie **czujki** zawsze są wyświetlane zmienne, które są obserwowane (są wyszarzone, gdy są poza zakresem).

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

1. W pętli `for` kliknij okno **stos wywołań** , które jest domyślnie otwarte w prawym dolnym okienku.

    Jeśli jest zamknięte, otwórz je podczas wstrzymania w debugerze, wybierając pozycję **debuguj** > **Windows** > **stos wywołań**.

2. Klikaj polecenie **F11** kilka razy, aż zobaczysz debuger pauzy w metodzie `SendMessage`. Sprawdź okno **stosu wywołań** .

    ![Badanie stosu wywołań](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Okno **stos wywołań** pokazuje kolejność, w której metody i funkcje są wywoływane. W górnym wierszu jest wyświetlana bieżąca funkcja (Metoda `SendMessage` w tej aplikacji). Drugi wiersz pokazuje, że `SendMessage` został wywołany z metody `main` i tak dalej.

   > [!NOTE]
   > Okno **stosu wywołań** przypomina perspektywę debugowania w niektórych środowisk IDE, takich jak przezaćmienie.

    Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przyjrzeć się kodu źródłowego i zmienia także bieżący zakres kontrolowanym przez debuger. Ta akcja nie wcześniejsze debugera.

    Możesz również użyć menu dostępnych po kliknięciu prawym przyciskiem myszy w oknie **stos wywołań** , aby wykonać inne czynności. Na przykład można wstawiać punkty przerwania do określonych funkcji, przełączać debuger za pomocą polecenia **Uruchom do kursora**i testować kod źródłowy. Aby uzyskać więcej informacji, zobacz [How to: badanie stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

1. Naciśnij dwukrotnie klawisz **F11** , aby uruchomić funkcję `std::wcout`.

1. Po wstrzymaniu debugera w wywołaniu metody `SendMessage` Użyj myszy, aby uzyskać żółtą strzałkę (wskaźnik wykonywania) po lewej stronie, a następnie przesuń żółtą strzałkę w górę o jeden wiersz w górę, z powrotem do `std::wcout`.

1. Naciśnij klawisz **F11**.

    Debuger uruchamia ponownie funkcję `std::wcout` (zobaczysz to w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonania, można wykonać czynności, jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często muszą być ostrożnym z tej funkcji, a następnie zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

1. Naciśnij klawisz **F5** , aby kontynuować uruchamianie aplikacji.

    Gratulujemy wykonanie kroków tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)

