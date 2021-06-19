---
title: 'Samouczek: debugowanie kodu C#'
description: Poznaj funkcje debugera języka Visual Studio oraz dowiedz się, jak uruchomić debuger, przechodzić przez kod i sprawdzać dane w aplikacji języka C#.
ms.custom: debug-experiment, vs-acquisition, get-started
ms.date: 04/23/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fe0c698ce1263713a758bd98fba49433b3ff511
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390284"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: nauka debugowania kodu C# przy użyciu Visual Studio

W tym artykule przedstawimy funkcje debugera Visual Studio w przewodniku krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [Pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Podczas *debugowania aplikacji* zwykle oznacza to, że aplikacja jest uruchamiana z dołączonym debugerem. Gdy to zrobisz, debuger udostępnia wiele sposobów na zobaczenie działania kodu podczas jego działania. Możesz przejść przez kod i przyjrzeć się wartościom przechowywanym w zmiennych, ustawić wyglądać zmienne, aby zobaczyć, kiedy wartości zmieniają się, zbadać ścieżkę wykonywania kodu, sprawdzić, czy gałąź kodu jest uruchomiona i tak dalej. Jeśli po raz pierwszy próbujesz debugować kod, przed rozpoczęciem tego artykułu warto przeczytać artykuł [Debugowanie](../../debugger/debugging-absolute-beginners.md) dla bezwzględnych początkujących.

Mimo że aplikacja demonstracyjna to C#, większość funkcji ma zastosowanie do języków C++, Visual Basic, F#, Python, JavaScript i innych języków obsługiwanych przez program Visual Studio (język F# nie obsługuje funkcji Edit-and-continue. Język F# i język JavaScript nie obsługują **okna Automatyczne).** Zrzuty ekranu znajdują się w języku C#.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i naciśnij punkty przerwania.
> * Poznasz polecenia umożliwiające krok po kroku kod w debugerze
> * Sprawdzanie zmiennych w oknach porad dotyczących danych i debugera
> * Badanie stosu wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany Visual Studio 2019 r. i międzyplatformowe obciążenie tworzenia **aplikacji na platformie .NET Core.**

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany Visual Studio 2017 r. i międzyplatformowe obciążenie tworzenie aplikacji **na platformie .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsolowej .NET Core. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek do ciebie dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj projektowi *nazwę get-started-debugging.*

     Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** wybierz **link** Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt.

     Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Jeśli okno uruchamiania nie jest  otwarte, wybierz pozycję > **Okno uruchamiania pliku.**

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa** dla platformy .NET Core, a następnie wybierz pozycję **Dalej.**

   ![Wybieranie szablonu języka C# dla aplikacji konsolowej](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli,** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji. Następnie w chmurze Instalator programu Visual Studio obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.**

1. W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *GetStartedDebugging* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

1. Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz **pozycję Utwórz.**

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *programie Program.cs* zastąp cały kod domyślny następującym kodem:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij **klawisz F5** **(Debuguj > Rozpocznij debugowanie)** lub przycisk **Rozpocznij** debugowanie ![Na](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") pasku narzędzi debugowania.

     **Klawisz F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale w tej chwili nie zrobiliśmy niczego specjalnego, aby przeanalizować kod. Aplikacja zostanie więc po prostu załadowana i zobaczysz dane wyjściowe konsoli.

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

     W tym samouczku przyjrzymy się bliżej tej aplikacji przy użyciu debugera i zobaczymy funkcje debugera.

2. Zatrzymaj debuger, naciskając czerwony przycisk ![Zatrzymaj debugowanie](../../debugger/media/dbg-tour-stop-debugging.png "Zatrzymywanie debugowania") **(Shift**  +  **F5).**

3. W oknie konsoli naciśnij klawisz, aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

1. W pętli funkcji ustaw punkt przerwania, klikając lewy `for` `Main` margines następującego wiersza kodu:

    `name += letters[i];`

    W miejscu ustawienia ![punktu](../../debugger/media/dbg-breakpoint.png "Punkt przerwania") przerwania zostanie wyświetlony czerwony punkt przerwania.

    Punkty przerwania to jedna z najbardziej podstawowych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub temu, czy gałąź kodu jest uruchamiana.

2. Naciśnij **klawisz F5** lub przycisk **Rozpocznij** debugowanie Rozpocznij debugowanie, aplikacja zostanie uruchomiona, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawisz punkt przerwania. ![](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie")

    ![Ustawianie i trafianie punktu przerwania](../csharp/media/get-started-set-breakpoint.gif)

    Żółta strzałka reprezentuje instrukcje, na których debuger został wstrzymany, co również wstrzymuje wykonywanie aplikacji w tym samym momencie (ta instrukcja nie została jeszcze wykonana).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **klawisz F5** uruchamia debuger i zatrzymuje się w pierwszym punkcie przerwania. W przeciwnym **razie klawisz F5** kontynuuje uruchamianie aplikacji do następnego punktu przerwania.

    Punkty przerwania są przydatną funkcją, gdy znasz wiersz kodu lub sekcję kodu, którą chcesz dokładnie zbadać. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Używanie punktów przerwania](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Nawigowanie po kodzie i sprawdzanie danych przy użyciu porad dotyczących danych

W większości używamy tutaj skrótów klawiaturowych, ponieważ jest to dobry sposób na szybkie wykonywanie aplikacji w debugerze (równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

1. Po wstrzymaniu instrukcji zatrzymaj wskaźnik myszy na zmiennej i zobaczysz, że jest to wartość domyślna, czyli wartość pierwszego `name += letters[i]` `letters` elementu w tablicy `char[10]` .

     Funkcje, które umożliwiają sprawdzanie zmiennych, są jedną z najbardziej przydatnych funkcji debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz dowiedzieć się, czy zmienne przechowują wartości, których oczekujesz w określonym czasie.

1. Rozwiń `letters` zmienną, aby wyświetlić jej właściwości, które obejmują wszystkie elementy, które zawiera zmienna.

     ![Zrzut ekranu Visual Studio debugera z wyróżnionej instrukcji "name+= letters[I]" i listą rozwijaną przedstawiającą elementy w tablicy liter.](../csharp/media/get-started-view-data-tip.png)

1. Następnie zatrzymaj wskaźnik myszy na zmiennej `name` i zobaczysz jej bieżącą wartość, czyli pusty ciąg.

1. Naciśnij dwukrotnie klawisz **F10** (lub wybierz pozycję **>** debuguj krok po kroku), aby przejść do wywołania metody, a następnie jeszcze raz naciśnij `SendMessage` klawisz **F10.**

     Klawisz F10 umożliwia przechodzenie do następnej instrukcji bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod jest nadal wykonywany). Po naciśnięciu klawisza F10 w wywołaniu metody pominięto kod implementacji (który może nas w tej chwili `SendMessage` `SendMessage` nie interesuje).

1. Naciśnij kilka razy klawisz **F10** (lub Debuguj krok po kroku), aby kilka razy iterować po pętli, wsłuchiwać ponownie w punkcie przerwania i za każdym razem umieszczać kursor nad zmienną, aby sprawdzić jej  >   `for` `name` wartość.

     ![Animowany zrzut ekranu przedstawiający Visual Studio debugera pokazujący efekt naciśnięcia klawisza F10 do "Przekrzuć" i iterowania przez pętlę podczas debugowania.](../csharp/media/get-started-data-tip.gif)

     Wartość zmiennej zmienia się z każdą iteracją pętli, pokazując wartości `for` , następnie , następnie , i tak `f` `fr` `fre` dalej. Aby przyspieszyć pracę debugera w pętli w tym scenariuszu, możesz nacisnąć klawisz **F5** (lub wybrać pozycję Debuguj kontynuuj), co pozwala przejść do punktu przerwania zamiast  >  następnej instrukcji.

     Często podczas debugowania chcesz szybko sprawdzić wartości właściwości zmiennych, aby sprawdzić, czy przechowują one wartości, które powinny być przechowywane, a porady dotyczące danych są dobrym sposobem na to.

1. Mimo że metoda jest nadal wstrzymana w pętli, naciśnij klawisz `for` `Main` **F11** (lub wybierz pozycję **Debuguj**> Step Into ) do momentu wstrzymania w `SendMessage` wywołaniu metody.

     Powinien być w tym wierszu kodu:

     `SendMessage(name, a[i]);`

1. Naciśnij **jeszcze raz klawisz F11,** aby wejściować do metody `SendMessage` .

     Żółty wskaźnik przesuwa się do `SendMessage` metody .

     ![Używanie klawisza F11 do wejściowego do kodu](../csharp/media/get-started-f11.png "F10 Step Into")

     Klawisz F11 to polecenie **Step Into,** które umożliwia wykonywanie aplikacji po jednej instrukcji na raz. F11 to dobry sposób na szczegółowe zbadanie przepływu wykonywania. Domyślnie debuger pomija kod niebędący użytkownikiem (jeśli chcesz uzyskać więcej szczegółów, zobacz [Tylko mój kod](../../debugger/just-my-code.md)).

     Załóżmy, że wszystko jest gotowe do zbadania metody i chcesz wyjść z `SendMessage` metody, ale pozostać w debugerze. Możesz to zrobić za pomocą polecenia **Wyetapuj.**

1. Naciśnij **klawisz Shift**  +  **F11** (lub **debuguj > wyjść).**

     To polecenie wznawia wykonywanie aplikacji (i umożliwia postęp debugera) do momentu powrotu bieżącej metody lub funkcji.

     Powinien nawrócić pętlę `for` w `Main` metodzie , wstrzymany w wywołaniu `SendMessage` metody . Aby uzyskać więcej informacji na temat różnych sposobów przechodzenia przez kod, zobacz [Navigate code in the debugger (Nawigowanie po kodzie w debugerze).](../../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Nawigowanie po kodzie przy użyciu funkcji Uruchom do kliknięcia

1. Naciśnij **klawisz F5,** aby ponownie przejść do punktu przerwania.

1. W edytorze kodu przewiń w dół i umieść kursor nad metodą w metodzie do momentu, aż po lewej stronie pojawi się zielony przycisk Uruchom do kliknięcia `Console.WriteLine` `SendMessage` Uruchom do kliknięcia.  ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Etykietka narzędzia przycisku zawiera tekst "Uruchom wykonywanie do tego miejscu".

     ![Korzystanie z funkcji Uruchom do kliknięcia](../csharp/media/get-started-run-to-click.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom do kliknięcia** jest nowy w programie [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Jeśli nie widzisz zielonego przycisku strzałki, użyj **klawisza F11** w tym przykładzie, aby przejść debuger w odpowiednie miejsce).

2. Kliknij przycisk **Uruchom do kliknięcia,** ![a następnie kliknij przycisk Uruchom, aby kliknąć pozycję](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger jest przekierowywowyny do `Console.WriteLine` metody .

    Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. **Funkcja Uruchom do kliknięcia** umożliwia szybkie poruszanie się w widocznym regionie kodu aplikacji (możesz kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Restart** ![Restart App (Uruchom ponownie](../../debugger/media/dbg-tour-restart.png "RestartApp") ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5).**

Naciśnięcie przycisku **Uruchom ponownie** pozwala zaoszczędzić czas w porównaniu z zatrzymywaniem aplikacji i ponownym uruchamianiem debugera. Debuger jest wstrzymywany w pierwszym punkcie przerwania, który zostanie trafiony przez wykonanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania, który został wcześniej ustawiony wewnątrz `for` pętli.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Spójrz na **okno Automatyczne** w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając opcję  >  **Debuguj automatyczne**  >  **systemy** Windows.

    W **oknie Automatyczne** zobaczysz zmienne i ich bieżącą wartość. Okno **Automatyczne wyświetla** wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (sprawdź dokumentację pod celu sprawdzenia zachowania specyficznego dla języka).

1. Następnie przyjrzyj się **oknie Locals (Ustawienia** lokalne) na karcie obok **okna Autos (Automatyczne).**

1. Rozwiń `letters` zmienną, aby wyświetlić elementy, które zawiera.

     ![Sprawdzanie zmiennych w oknie Zmiennych lokalnych](../csharp/media/get-started-locals-window.png "Okno lokalizacji lokalnych")

    Okno **Zmienne lokalne** zawiera zmienne, które znajdują się w bieżącym zakresie , czyli bieżącym kontekście wykonywania. [](https://www.wikipedia.org/wiki/Scope_(computer_science))

## <a name="set-a-watch"></a>Ustawianie zegarka

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy `name` zmienną i wybierz polecenie **Dodaj czujkę.**

    W **dolnej** części edytora kodu zostanie otwarte okno Czujka. W oknie **Wyrażenie czujki** można określić zmienną (lub wyrażenie), którą chcesz śledzić.

    Teraz masz zegarek ustawiony na zmienną i możesz zobaczyć, jak jej wartość zmienia się podczas przechodzenia `name` przez debuger. W przeciwieństwie do innych  okien zmiennych, okno Czujka zawsze pokazuje obserwowane zmienne (są one wyszarowane, gdy są poza zakresem).

## <a name="examine-the-call-stack"></a>Badanie stosu wywołań

1. Po wstrzymaniu w pętli kliknij okno Stos wywołań, które jest domyślnie `for` otwarte w prawym dolnym okienku. 

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając **polecenie**  >  **Debuguj stos**  >  **wywołań systemu** Windows .

2. Klikaj **klawisz F11** kilka razy, aż w metodzie zostanie wyświetlony debuger wstrzymywany. `SendMessage` Spójrz na **okno Stos wywołań.**

    ![Badanie stosu wywołań](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Okno **Stos wywołań** pokazuje kolejność wywoływania metod i funkcji. Górny wiersz pokazuje bieżącą funkcję `SendMessage` (metodę w tej aplikacji). Drugi wiersz pokazuje, że `SendMessage` został wywołany z `Main` metody i tak dalej.

   > [!NOTE]
   > Okno **stosu wywołań jest** podobne do perspektywy debugowania w niektórych środowiskach PROJEKTOWYCH, takich jak Eclipse.

    Stos wywołań to dobry sposób na zbadanie i zrozumienie przepływu wykonywania aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przejść do tego kodu źródłowego i zmienić bieżący zakres sprawdzany przez debuger. Ta akcja nie powoduje postępu debugera.

    Możesz również użyć menu otwieranych prawym przyciskiem myszy w **oknie stosu wywołań,** aby wykonać inne czynności. Możesz na przykład wstawić punkty przerwania do określonych funkcji, przejść do debugera za pomocą polecenia **Uruchom** do kursora i przejść do kodu źródłowego. Aby uzyskać więcej informacji, [zobacz How to: Examine the Call Stack](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmienianie przepływu wykonywania

1. Naciśnij dwukrotnie klawisz **F11,** aby uruchomić `Console.WriteLine` metodę .

1. Po wstrzymaniu debugera w wywołaniu metody użyj myszy, aby chwycić żółtą strzałkę (wskaźnik wykonywania) po lewej stronie i przenieść żółtą strzałkę w górę o jedną linię z powrotem do `SendMessage` `Console.WriteLine` .

1. Naciśnij **klawisz F11**.

    Debuger ponownie uruchomić metodę `Console.WriteLine` (widać to w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonywania, możesz na przykład przetestować różne ścieżki wykonywania kodu lub ponownie uruchomić kod bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często należy zachować ostrożność podczas pracy z tą funkcją i w etykietce narzędzia jest wyświetlane ostrzeżenie. Mogą pojawić się również inne ostrzeżenia. Przeniesienie wskaźnika nie może przywrócić wcześniejszego stanu aplikacji.

1. Naciśnij **klawisz F5,** aby kontynuować uruchamianie aplikacji.

    Gratulujemy ukończenia tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku nauczyliśmy się uruchamiać debuger, przechodzić przez kod i sprawdzać zmienne. Możesz chcieć uzyskać szczegółowe informacje na temat funkcji debugera wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
