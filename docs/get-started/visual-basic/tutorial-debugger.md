---
title: 'Samouczek: debugowanie Visual Basic kodu'
description: Poznaj funkcje debugera Visual Studio, jak uruchomić debuger, przechodzić przez kod i sprawdzać dane w Visual Basic aplikacji.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/03/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42dd3c6b7301162e239bc87764056fdda2d08413
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308418"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Samouczek: nauka debugowania kodu Visual Basic użyciu Visual Studio

Ten artykuł zawiera wprowadzenie do funkcji debugera Visual Studio w przewodniku krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [Pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Debugowanie *aplikacji zwykle* oznacza, że aplikacja jest uruchamiana z dołączonym debugerem. Gdy to zrobisz, debuger udostępnia wiele sposobów na zobaczenie działania kodu podczas jego działania. Możesz przejść przez kod i przyjrzeć się wartościom przechowywanym w zmiennych, ustawić wyglądać zmienne, aby zobaczyć, kiedy wartości zmieniają się, zbadać ścieżkę wykonywania kodu, sprawdzić, czy gałąź kodu jest uruchomiona i tak dalej. Jeśli po raz pierwszy próbujesz debugować kod, przed rozpoczęciem [](../../debugger/debugging-absolute-beginners.md) tego artykułu warto przeczytać artykuł Debugowanie dla bezwzględnych początkujących użytkowników.

Mimo że aplikacja demonstracyjna jest Visual Basic, większość funkcji ma zastosowanie do języków C#, C++, F#, Python, JavaScript i innych języków obsługiwanych przez program Visual Studio (język F# nie obsługuje funkcji Edytuj i kontynuuj. Język F# i język JavaScript nie obsługują **okna Automatyczne).** Zrzuty ekranu znajdują się Visual Basic.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i naciśnij punkty przerwania.
> * Poznasz polecenia umożliwiające krokowe przechodzinie przez kod w debugerze
> * Sprawdzanie zmiennych w oknach porad dotyczących danych i debugera
> * Badanie stosu wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany program Visual Studio 2019 r. i obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.**

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany program Visual Studio 2017 i międzyplatformowe obciążenie deweloperski platformy **.NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsolowej .NET Core. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie **rozwiń** pozycję Visual Basic , a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj projektowi *nazwę get-started-debugging.*

     Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** wybierz link **Otwórz** Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt.

     Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję **Okno** > **uruchamiania pliku.**

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

1. W **oknie Create a new project (Tworzenie** nowego projektu) wprowadź lub wpisz *console* (konsola) w polu wyszukiwania. Następnie wybierz **pozycję Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsoli** dla platformy .NET Core, a następnie wybierz pozycję **Dalej.**

   ![Wybierz szablon Visual Basic aplikacji konsolowej](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli,** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji. Następnie w chmurze Instalator programu Visual Studio obciążenie Tworzenie aplikacji dla wielu platform dla **platformy .NET Core.**

1. W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *get-started-debugging* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

1. Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**

   Visual Studio otworzy nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *programie Program.vb* zastąp cały kod domyślny następującym kodem:

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij **klawisz F5** (Debuguj **> Rozpocznij debugowanie)** lub przycisk **Rozpocznij** ![debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

     **Klawisz F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale w tej chwili nie zrobiliśmy nic specjalnego, aby przeanalizować kod. Aplikacja po prostu się ładuje, a zobaczysz dane wyjściowe konsoli.

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

3. W oknie konsoli naciśnij klawisz , aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

1. W pętli funkcji ustaw punkt przerwania, klikając lewy `For` `Main` margines następującego wiersza kodu:

    `name += letters(i)`

    W miejscu ustawienia ![punktu](../../debugger/media/dbg-breakpoint.png "Punkt przerwania") przerwania pojawi się punkt przerwania z czerwonym okręgiem.

    Punkty przerwania są jedną z najbardziej podstawowych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub czy jest uruchamiana gałąź kodu.

2. Naciśnij **klawisz F5** lub ![](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie")przycisk **Rozpocznij** debugowanie Rozpocznij debugowanie, aplikacja zostanie uruchomiona, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawisz punkt przerwania.

    ![Ustawianie i trafianie punktu przerwania](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Żółta strzałka reprezentuje instrukcje, na których debuger został wstrzymany, co również wstrzymuje wykonywanie aplikacji w tym samym momencie (ta instrukcja nie została jeszcze wykonana).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **klawisz F5** uruchamia debuger i zatrzymuje się w pierwszym punkcie przerwania. W przeciwnym **razie klawisz F5** kontynuuje uruchamianie aplikacji do następnego punktu przerwania.

    Punkty przerwania są przydatną funkcją, gdy znasz wiersz kodu lub sekcję kodu, którą chcesz szczegółowo zbadać. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Using breakpoints](../../debugger/using-breakpoints.md)(Używanie punktów przerwania).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Nawigowanie po kodzie w debugerze przy użyciu poleceń kroku

W tym miejscu używamy przede wszystkim skrótów klawiaturowych, ponieważ jest to dobry sposób na szybkie wykonywanie aplikacji w debugerze (równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

1. Po wstrzymaniu w pętli w metodzie naciśnij dwukrotnie klawisz `For` `Main` **F11** (lub wybierz pozycję > debuguj do ), aby przejść do `SendMessage` wywołania metody.

     Po **dwukrotnym naciśnięciu klawisza F11** powinien być w tym wierszu kodu:

     `SendMessage(name, a(i))`

1. Naciśnij **jeszcze raz klawisz F11,** aby uzyskać dostęp do metody `SendMessage` .

     Żółty wskaźnik przesuwa się do `SendMessage` metody .

     ![Używanie klawisza F11 do wejścia do kodu](../visual-basic/media/get-started-f11-vb.png "F10 Step Into")

     Klawisz F11 to polecenie **Step Into,** które umożliwia postęp wykonywania aplikacji po jednej instrukcji na raz. F11 to dobry sposób na szczegółowe zbadanie przepływu wykonywania. (Aby szybciej przechodzić przez kod, pokazujemy również inne opcje). Domyślnie debuger pomija kod niebędący użytkownikiem (jeśli chcesz uzyskać więcej szczegółów, zobacz [Tylko mój kod](../../debugger/just-my-code.md)).

     Załóżmy, że po zapoznaniu się z metodą chcesz wyjść z metody, ale `SendMessage` pozostać w debugerze. Możesz to zrobić za pomocą polecenia **Wyetapuj.**

1. Naciśnij **klawisz Shift**  +  **F11** (lub **Debuguj > wyetapiuj**).

     To polecenie wznawia wykonywanie aplikacji (i postępuje debuger) do momentu, gdy bieżąca metoda lub funkcja zostanie przywrócona.

     Powinien nawrócić pętlę `For` w `Main` metodzie , wstrzymany w wywołaniu `SendMessage` metody .

1. Naciśnij **klawisz F11** kilka razy, aż wrócisz ponownie `SendMessage` do wywołania metody.

1. Po wstrzymaniu w wywołaniu metody naciśnij **klawisz F10** (lub wybierz > **Przekłoń**) raz.

     ![Używanie klawisza F10 do przekłócenia kodu](../visual-basic/media/get-started-step-over-vb.png "F10 Step Over")

     Zauważ, że tym razem debuger nie wchodzi do `SendMessage` metody . **Klawisz F10** umożliwia postęp debugera bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod jest nadal wykonywany). Naciskając klawisz **F10** w wywołaniu metody `SendMessage` (zamiast **klawisza F11),** pominąliśmy kod implementacji dla metody (co może nas w tej chwili `SendMessage` nie interesuje). Aby uzyskać więcej informacji na temat różnych sposobów przechodzenia przez kod, zobacz [Navigate code in the debugger (Nawigowanie po kodzie w debugerze).](../../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Nawigowanie po kodzie przy użyciu funkcji Uruchom do kliknięcia

1. Naciśnij **klawisz F5,** aby ponownie przejść do punktu przerwania.

1. W edytorze kodu przewiń w dół i umieść kursor nad metodą w metodzie do momentu, aż po lewej stronie pojawi się zielony przycisk Uruchom do kliknięcia `Console.WriteLine` `SendMessage` Uruchom do kliknięcia.  ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Etykietka narzędzia przycisku zawiera tekst "Uruchom wykonywanie do tego miejscu".

     ![Korzystanie z funkcji Uruchom do kliknięcia](../visual-basic/media/get-started-run-to-click-vb.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom do kliknięcia** jest nowy w programie [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Jeśli nie widzisz zielonego przycisku strzałki, użyj **klawisza F11** w tym przykładzie, aby przejść debuger w odpowiednie miejsce).

2. Kliknij przycisk **Uruchom do kliknięcia,** ![a następnie kliknij przycisk Uruchom, aby kliknąć pozycję](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger jest przekierowywowyny do `Console.WriteLine` metody .

    Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. **Funkcja Uruchom do kliknięcia** umożliwia szybkie poruszanie się w widocznym regionie kodu aplikacji (możesz kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Restart** ![Restart App (Uruchom ponownie](../../debugger/media/dbg-tour-restart.png "RestartApp") ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5).**

Naciśnięcie przycisku **Uruchom ponownie** pozwala zaoszczędzić czas w porównaniu z zatrzymywaniem aplikacji i ponownym uruchamianiem debugera. Debuger jest wstrzymywany w pierwszym punkcie przerwania, który zostanie trafiony przez wykonanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania, który został wcześniej ustawiony wewnątrz `For` pętli.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych za pomocą porad dotyczących danych

Funkcje, które umożliwiają sprawdzanie zmiennych, są jedną z najbardziej przydatnych funkcji debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz dowiedzieć się, czy zmienne przechowują wartości, których oczekujesz w określonym czasie.

1. Po wstrzymaniu instrukcji umieść kursor nad zmienną i zobaczysz, że jest to wartość domyślna, czyli wartość pierwszego `name += letters[i]` `letters` elementu w tablicy `"f"c` .

1. Następnie umieść kursor nad `name` zmienną i zobaczysz jej bieżącą wartość, czyli pusty ciąg.

1. Naciśnij kilka razy klawisz **F5** (lub Kontynuuj debugowanie), aby kilka razy iterować po pętli, wsłuchiwać się ponownie w punkcie przerwania i za każdym razem umieszczać kursor nad zmienną, aby sprawdzić jej  >   `For` `name` wartość.

     ![Wyświetlanie porady dotyczącej danych](../visual-basic/media/get-started-data-tip-vb.png "Wyświetlanie porady dotyczącej danych")

     Wartość zmiennej zmienia się z każdą iteracją pętli, pokazując wartości `For` , następnie , następnie , i tak `f` `fr` `fre` dalej.

     Często podczas debugowania chcesz szybko sprawdzić wartości właściwości zmiennych, aby sprawdzić, czy przechowują one wartości, które powinny być przechowywane, a porady dotyczące danych są dobrym sposobem na to.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Spójrz na **okno Automatyczne** w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając opcję  >  **Debuguj automatyczne**  >  **systemy** Windows.

    W **oknie Automatyczne** zobaczysz zmienne i ich bieżącą wartość. Okno **Automatyczne wyświetla** wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (sprawdź dokumentację pod celu sprawdzenia zachowania specyficznego dla języka).

1. Następnie przyjrzyj się **oknie Locals (Ustawienia** lokalne) na karcie obok **okna Autos (Automatyczne).**

1. Rozwiń `letters` zmienną, aby wyświetlić elementy, które zawiera.

     ![Sprawdzanie zmiennych w oknie Zmiennych lokalnych](../visual-basic/media/get-started-locals-window-vb.png "Okno lokalizacji lokalnych")

    Okno **Zmienne lokalne** zawiera zmienne, które znajdują się w bieżącym zakresie , czyli bieżącym kontekście wykonywania. [](https://www.wikipedia.org/wiki/Scope_(computer_science))

## <a name="set-a-watch"></a>Ustawianie zegarka

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy `name` zmienną i wybierz polecenie **Dodaj czujkę.**

    W **dolnej** części edytora kodu zostanie otwarte okno Czujka. W oknie **Wyrażenie czujki** można określić zmienną (lub wyrażenie), którą chcesz śledzić.

    Teraz masz zegarek ustawiony na zmienną i możesz zobaczyć, jak jej wartość zmienia się podczas przechodzenia `name` przez debuger. W przeciwieństwie do innych  okien zmiennych, okno Czujka zawsze pokazuje obserwowane zmienne (są one wyszarowane, gdy są poza zakresem).

## <a name="examine-the-call-stack"></a>Badanie stosu wywołań

1. Po wstrzymaniu w pętli kliknij okno Stos wywołań, które jest domyślnie `For` otwarte w prawym dolnym okienku. 

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając **polecenie**  >  **Debuguj stos**  >  **wywołań systemu** Windows .

2. Klikaj **klawisz F11** kilka razy, aż w metodzie zostanie wyświetlony debuger wstrzymywany. `SendMessage` Spójrz na **okno Stos wywołań.**

    ![Badanie stosu wywołań](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

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
