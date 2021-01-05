---
title: 'Samouczek: Debugowanie kodu C#'
description: Dowiedz się więcej o funkcjach debugera programu Visual Studio oraz o sposobie uruchamiania debugera, przechodzenia przez kod i inspekcji danych w aplikacji języka C#.
ms.custom: debug-experiment, seodec18, get-started
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 435564a9bf4e90dd25ed5fee3a44d0578c201a99
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846939"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: informacje na temat debugowania kodu w języku C# przy użyciu programu Visual Studio

W tym artykule wprowadzono funkcje debugera programu Visual Studio w przewodniku krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Gdy *debugujesz aplikację*, zazwyczaj oznacza to, że aplikacja jest uruchamiana z dołączonym debugerem. Po wykonaniu tej czynności debuger zapewnia wiele sposobów, aby zobaczyć, co Twój kod działa podczas jego uruchamiania. Możesz przechodzić przez kod i przeglądać wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmieniają się wartości, można sprawdzić ścieżkę wykonywania kodu, sprawdzić, czy gałąź kodu jest uruchomiona itd. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przejściem do tego artykułu warto przeczytać [debugowanie dla bezwzględnych początkujących](../../debugger/debugging-absolute-beginners.md) .

Mimo że aplikacja demonstracyjna to C#, większość funkcji ma zastosowanie do języków C++, Visual Basic, F #, Python, JavaScript i innych obsługiwanych przez program Visual Studio (F # nie obsługuje funkcji Edit-and-Continue. Języka F # i języka JavaScript nie obsługują okna **autostarts** ). Zrzuty ekranu znajdują się w języku C#.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom Debuger i naciśnij punkty przerwania.
> * Informacje o poleceniach do przechodzenia przez kod w debugerze
> * Inspekcja zmiennych w oknach etykietek danych i debugera
> * Badanie stosu wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany program Visual Studio 2019 i **Międzyplatformowe obciążenie dla programu .NET Core** .

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany program Visual Studio 2017 i **Międzyplatformowe obciążenie dla programu .NET Core** .

::: moniker-end

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsolowej .NET Core. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nadaj nazwę projekt *Get-Started-Debug*.

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

     Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

   Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik** > **startowy**.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie szablonu C# dla aplikacji konsolowej (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *GetStartedDebugging* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   Program Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W programie *program.cs* zamiast tego Zastąp cały kod domyślny następującym kodem:

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

## <a name="start-the-debugger"></a>Uruchom Debuger.

1. Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

     **F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale teraz nie robimy żadnych specjalnych, aby przeanalizować kod. Dzięki temu aplikacja jest ładowana i zobaczysz dane wyjściowe konsoli.

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

     W tym samouczku przejdziemy bliżej tej aplikacji przy użyciu debugera i zapoznajesz się z funkcjami debugera.

2. Zatrzymaj debuger, naciskając czerwony przycisk Zatrzymaj ![debugowanie](../../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") (**SHIFT**  +  **F5**).

3. W oknie konsoli naciśnij klawisz, aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

1. W `for` pętli `Main` funkcji Ustaw punkt przerwania, klikając lewy margines w następującym wierszu kodu:

    `name += letters[i];`

    W miejscu ustawionym na ![punkt przerwania pojawia się](../../debugger/media/dbg-breakpoint.png "Punkt") czerwony okrąg.

    Punkty przerwania są jedną z najważniejszych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana.

2. Naciśnij klawisz **F5** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie"), uruchomienie aplikacji, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawiono punkt przerwania.

    ![Ustaw i naciśnij punkt przerwania](../csharp/media/get-started-set-breakpoint.gif)

    Żółta strzałka reprezentuje instrukcję, na której debuger wstrzymał działanie, co również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie została jeszcze wykonana).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchamia debuger i kończy się przy pierwszym punkcie przerwania. W przeciwnym razie **F5** kontynuuje działanie aplikacji do następnego punktu przerwania.

    Punkty przerwania są przydatną funkcją, gdy znasz wiersz kodu lub sekcję kodu, który chcesz szczegółowo sprawdzić. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Używanie punktów przerwania](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Nawigowanie po kodzie i sprawdzanie danych przy użyciu porad dotyczących danych

W większości przypadków używamy skrótów klawiaturowych w tym miejscu, ponieważ jest dobrym sposobem na szybkie wykonywanie aplikacji w debugerze (równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

1. Po wstrzymaniu w `name += letters[i]` instrukcji Umieść wskaźnik myszy nad `letters` zmienną i zobaczysz jej wartość domyślną, wartość pierwszego elementu w tablicy `char[10]` .

     Funkcje, które umożliwiają inspekcję zmiennych, są jedną z najbardziej przydatnych funkcji debugera i istnieją różne sposoby ich wykonania. Często podczas próby debugowania problemu próbujesz dowiedzieć się, czy zmienne przechowują wartości oczekiwane w określonym czasie.

1. Rozwiń `letters` zmienną, aby wyświetlić jej właściwości, które obejmują wszystkie elementy, które zawiera zmienna.

     ![Zrzut ekranu debugera programu Visual Studio z wyróżnioną instrukcją "name + = litery [I]" oraz listą rozwijaną przedstawiającą elementy w tablicy litery.](../csharp/media/get-started-view-data-tip.png)

1. Następnie umieść wskaźnik myszy nad `name` zmienną i zobaczysz jej bieżącą wartość, pusty ciąg.

1. Naciśnij klawisz **F10** (lub wybierz polecenie **Debuguj >** przekroczenie) dwukrotnie, aby przejść do `SendMessage` wywołania metody, a następnie naciśnij klawisz **F10** jeszcze raz.

     F10 przesuwa debuger do następnej instrukcji bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod nadal jest wykonywany). Naciskając klawisz F10 w `SendMessage` wywołaniu metody, pominął kod implementacji dla `SendMessage` (co może nie interesuje Cię teraz).

1. Naciśnij klawisz **F10** (lub **Debuguj**  >  **krokowo**) kilka razy, aby wielokrotnie wykonać iterację w `for` pętli, zatrzymując ponownie w punkcie przerwania i umieścić wskaźnik myszy nad `name` zmienną za każdym razem, aby sprawdzić jej wartość.

     ![Animowany zrzut ekranu debugera programu Visual Studio pokazujący efekt naciskania klawisza F10 na "krok po kroku" i Iterowanie przez pętlę podczas debugowania.](../csharp/media/get-started-data-tip.gif)

     Wartość zmiennej zmienia się z każdą iteracją `for` pętli, wyświetlając wartości `f` , then, `fr` `fre` i tak dalej. Aby szybciej korzystać z debugera przez pętlę w tym scenariuszu, możesz nacisnąć klawisz **F5** (lub wybrać polecenie **Debuguj**  >  **dalej**), co spowoduje przejście do punktu przerwania zamiast następnej instrukcji.

     Często podczas debugowania chcesz szybko sprawdzić wartości właściwości w zmiennych, aby sprawdzić, czy przechowują wartości, które oczekują na przechowywanie, a porady dotyczące danych to dobry sposób na to.

1. Mimo że wstrzymano w `for` pętli w `Main` metodzie, naciśnij klawisz **F11** (lub wybierz polecenie **Debuguj > Wkrocz**) do momentu wstrzymania w `SendMessage` wywołaniu metody.

     Należy mieć następujący wiersz kodu:

     `SendMessage(name, a[i]);`

1. Naciśnij klawisz **F11** jeszcze raz, aby przejść do `SendMessage` metody.

     Żółty wskaźnik jest zaawansowany do `SendMessage` metody.

     ![Użyj klawisza F11, aby przejść do kodu](../csharp/media/get-started-f11.png "Wkrocz do kroku")

     F11 to **krok do** polecenia i postępuje z jedną instrukcją wykonywania aplikacji w danym momencie. F11 jest dobrym sposobem na badanie przepływu wykonywania w najbardziej szczegółowy sposób. Domyślnie debuger pomija kod niebędący użytkownikiem (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../../debugger/just-my-code.md)).

     Załóżmy, że skończysz badanie `SendMessage` metody i chcesz uzyskać dostęp do metody, ale pozostać w debugerze. Można to zrobić przy użyciu polecenia **krok po kroku** .

1. Naciśnij klawisz **SHIFT**  +  **F11** (lub **Debuguj > krok wychodzący**).

     To polecenie wznawia wykonywanie aplikacji (i zwiększa debuger) do momentu, gdy bieżąca metoda lub funkcja zwróci wynik.

     Należy wrócić do `for` pętli w `Main` metodzie, wstrzymane przy `SendMessage` wywołaniu metody. Aby uzyskać więcej informacji na temat różnych sposobów poruszania się po kodzie, zobacz [nawigowanie po kodzie w debugerze](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Nawigowanie po kodzie za pomocą polecenia Uruchom do kliknięcia

1. Naciśnij klawisz **F5** , aby ponownie przejść do punktu przerwania.

1. W edytorze kodu przewiń w dół i umieść kursor nad `Console.WriteLine` metodą w `SendMessage` metodzie do momentu,  gdy zielony przycisk Uruchom ![do kliknięcia](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") zostanie wyświetlony po lewej stronie. Etykietka narzędzia dla przycisku pokazuje "uruchom wykonywanie do tego miejsca".

     ![Korzystanie z funkcji uruchamiania do kliknięcia](../csharp/media/get-started-run-to-click.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom do kliknięcia** jest nowy w [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Jeśli nie widzisz przycisku Zielona strzałka, użyj klawisza **F11** w tym przykładzie zamiast, aby przejść do odpowiedniego miejsca w debugerze).

2. Kliknij przycisk **Uruchom, aby kliknąć** polecenie ![Uruchom, aby kliknąć](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger postępuje z tą `Console.WriteLine` metodą.

    Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. **Uruchamianie do kliknięcia** jest przydatne do szybkiego szybszego wprowadzania informacji w widocznym regionie kodu aplikacji (można kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Uruchom** ponownie ![Uruchom aplikację](../../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl**  +  **SHIFT**  +  **F5**).

Po naciśnięciu przycisku **Uruchom ponownie** program zapisze czas w przeciwieństwie do zatrzymywania aplikacji i ponownego uruchomienia debugera. Debuger zatrzymuje się w pierwszym punkcie przerwania, który jest wywoływany przez wykonanie kodu.

Debuger zatrzyma się ponownie w punkcie przerwania, który został wcześniej ustawiony wewnątrz `for` pętli.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspekcja zmiennych przy użyciu okienek Autostart i locale

1. Zapoznaj się z oknem **Autokorekty** u dołu edytora kodu.

    Jeśli jest zamknięte, otwórz je podczas wstrzymania w debugerze, wybierając pozycję **Debuguj**  >  **okna**  >  **autostartowe**.

    W oknie **Autokorekty** widoczne są zmienne i ich bieżąca wartość. W oknie **samochody** są wyświetlane wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (Sprawdź dokumentację zachowania specyficzną dla języka).

1. Następnie zapoznaj się z oknem **Locals (ustawienia regionalne** ) na karcie obok okna **Autokorekty** .

1. Rozwiń `letters` zmienną, aby wyświetlić elementy, które zawiera.

     ![Sprawdź zmienne w oknie zmiennych lokalnych](../csharp/media/get-started-locals-window.png "Okno zmiennych lokalnych")

    W oknie **Ustawienia lokalne** są wyświetlane zmienne, które znajdują się w bieżącym [zakresie](https://www.wikipedia.org/wiki/Scope_(computer_science)), czyli bieżącym kontekście wykonania.

## <a name="set-a-watch"></a>Ustawianie czujki

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy `name` zmienną i wybierz polecenie **Dodaj czujkę**.

    Zostanie otwarte okno **czujki** w dolnej części edytora kodu. Możesz użyć okna **czujki** , aby określić zmienną (lub wyrażenie), dla którego chcesz zachować czujkę.

    Teraz masz ustawiony element czujki dla `name` zmiennej i możesz zobaczyć jego zmianę wartości podczas przechodzenia przez debuger. W przeciwieństwie do innych zmiennych okien, w oknie **czujki** zawsze są wyświetlane zmienne, które są obserwowane (są wyszarzone, gdy są poza zakresem).

## <a name="examine-the-call-stack"></a>Badanie stosu wywołań

1. Po wstrzymaniu w `for` pętli kliknij okno **stos wywołań** , które jest domyślnie otwarte w prawym dolnym okienku.

    Jeśli jest zamknięte, otwórz je w debugerze, wybierając pozycję **Debuguj**  >    >  **stos wywołań** systemu Windows.

2. Klikaj polecenie **F11** kilka razy, aż zobaczysz debuger pauzy w `SendMessage` metodzie. Sprawdź okno **stosu wywołań** .

    ![Badanie stosu wywołań](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Okno **stos wywołań** pokazuje kolejność, w której metody i funkcje są wywoływane. Górny wiersz przedstawia bieżącą funkcję ( `SendMessage` metodę w tej aplikacji). Drugi wiersz pokazuje, że `SendMessage` został wywołany z `Main` metody i tak dalej.

   > [!NOTE]
   > Okno **stosu wywołań** przypomina perspektywę debugowania w niektórych środowisk IDE, takich jak przezaćmienie.

    Stos wywołań to dobry sposób, aby sprawdzić i zrozumieć przepływ wykonywania aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przejść do tego kodu źródłowego, a także zmienić bieżący zakres, który jest sprawdzany przez debuger. Ta akcja nie powoduje przejścia do debugera.

    Możesz również użyć menu dostępnych po kliknięciu prawym przyciskiem myszy w oknie **stos wywołań** , aby wykonać inne czynności. Na przykład można wstawiać punkty przerwania do określonych funkcji, przełączać debuger za pomocą polecenia **Uruchom do kursora** i testować kod źródłowy. Aby uzyskać więcej informacji, zobacz [How to: badanie stosu wywołań](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonywania

1. Naciśnij dwukrotnie klawisz **F11** , aby uruchomić `Console.WriteLine` metodę.

1. Po wstrzymaniu debugera w `SendMessage` wywołaniu metody Użyj myszy, aby uzyskać żółtą strzałkę (wskaźnik wykonywania) po lewej stronie, a następnie przesuń żółtą strzałkę w górę o jeden wiersz, z powrotem do `Console.WriteLine` .

1. Naciśnij klawisz **F11**.

    Debuger ponownie `Console.WriteLine` uruchamia metodę (zobaczysz to w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonywania, można wykonywać operacje, takie jak testowanie różnych ścieżek wykonywania kodu lub ponowne uruchamianie kodu bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często należy zachować ostrożność dzięki tej funkcji, a w etykietce narzędzia zostanie wyświetlone ostrzeżenie. Mogą również pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie może przywrócić aplikacji do wcześniejszego stanu aplikacji.

1. Naciśnij klawisz **F5** , aby kontynuować uruchamianie aplikacji.

    Gratulujemy ukończenia tego samouczka.

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, przewinąć kod i zbadać zmienne. Możesz chcieć uzyskać ogólne omówienie funkcji debugera oraz linki do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
