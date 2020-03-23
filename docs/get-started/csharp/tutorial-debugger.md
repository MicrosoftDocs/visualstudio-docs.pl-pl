---
title: 'Samouczek: Kod debugowania C#'
description: Dowiedz się, jak uruchomić debuger programu Visual Studio, przejść przez kod i sprawdzić dane.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 01/31/2020
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
ms.openlocfilehash: 6ede47c9daf37011195d66c746498cdfc809d24b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77027257"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: Naucz się debugować kod C# przy użyciu programu Visual Studio

W tym artykule przedstawiono funkcje debugera programu Visual Studio w przewodniku krok po kroku. Jeśli chcesz widok wyższego poziomu funkcji debugera, zobacz [Pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Podczas *debugowania aplikacji,* zwykle oznacza to, że aplikacja jest uruchomiona z dołączonym debugerem. Po wykonaniu tej funkcji debuger udostępnia wiele sposobów, aby zobaczyć, co robi kod podczas jego działania. Można przejść przez kod i spojrzeć na wartości przechowywane w zmiennych, można ustawić zegarki na zmienne, aby zobaczyć, kiedy zmiany wartości, można sprawdzić ścieżkę wykonywania kodu, sprawdzić, czy gałąź kodu jest uruchomiona i tak dalej. Jeśli jest to pierwszy raz, który próbowałeś debugować kod, możesz przeczytać [Debugowanie dla początkujących absolutnych](../../debugger/debugging-absolute-beginners.md) przed przejściem przez ten artykuł.

Mimo że aplikacja demonstracyjna jest C#, większość funkcji mają zastosowanie do języka C++, Visual Basic, F#, Python, JavaScript i innych języków obsługiwanych przez program Visual Studio (F# nie obsługuje edit-and-continue. F# i JavaScript nie obsługują okna **Autos).** Zrzuty ekranu są w języku C#.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i trafić punkty przerwania.
> * Dowiedz się, jak przejść przez kod w debugerze
> * Sprawdzanie zmiennych w poradach dotyczących danych i oknach debugera
> * Sprawdź stos wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musi być zainstalowany program Visual Studio 2019 i obciążenie **programistyczne .NET Core na wielu platformach.**

::: moniker-end
::: moniker range="vs-2017"

Musi być zainstalowany program Visual Studio 2017 i obciążenie **programistyczne .NET Core na wielu platformach.**

::: moniker-end

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsoli .NET Core. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij projekt *get-started-debugowania*.

     Jeśli nie widzisz szablonu projektu **aplikacji konsoli (NET Core),** wybierz łącze **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**

     Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

   Jeśli okno startowe nie jest otwarte, wybierz polecenie **Okno startowe** **pliku** > .

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# dla aplikacji konsoli (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji konsoli (.NET Core),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features** Następnie w Instalatorze programu Visual Studio wybierz obciążenie **programistyczne .NET Core na różnych platformach.**

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *GetStartedDebugging* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *Program.cs*zamiast tego zastąp cały kod domyślny następującym kodem:

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

1. Naciśnij **klawisz F5** **(Debugowanie > rozpocznij debugowanie)** lub przycisk **Start Debugowania** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi Debugowania.

     **F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale teraz nie zrobiliśmy nic specjalnego, aby zbadać kod. Więc aplikacja po prostu ładuje i widzisz wyjście konsoli.

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

     W tym samouczku przyjrzymy się bliżej tej aplikacji za pomocą debugera i przyjrzymy się funkcjom debugera.

2. Zatrzymaj debuger, naciskając czerwony przycisk ![zatrzymania debugowania](../../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") **(Shift** + **F5**).

3. W oknie konsoli naciśnij klawisz, aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

1. W `for` pętli `Main` funkcji ustaw punkt przerwania, klikając lewy margines następującego wiersza kodu:

    `name += letters[i];`

    W miejscu ustawiania punktu przerwania pojawi się ![czerwony punkt przerwania.](../../debugger/media/dbg-breakpoint.png "Punkt przerwania")

    Punkty przerwania są jedną z najbardziej podstawowych i podstawowych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany.

2. Naciśnij **klawisz F5** lub przycisk **Start Debugowania** ![Start Debugowania](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie"), aplikacja uruchamia się, a debuger uruchamia się do wiersza kodu, w którym można ustawić punkt przerwania.

    ![Ustawianie i trafienie punktu przerwania](../csharp/media/get-started-set-breakpoint.png)

    Żółta strzałka reprezentuje instrukcję, na której debuger wstrzymane, który również zawiesza wykonywanie aplikacji w tym samym momencie (ta instrukcja nie została jeszcze wykonana).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchamia debugera i zatrzymuje się w pierwszym punkcie przerwania. W przeciwnym razie **F5** kontynuuje uruchamianie aplikacji do następnego punktu przerwania.

    Punkty przerwania są przydatne funkcji, gdy znasz wiersz kodu lub sekcji kodu, które chcesz zbadać szczegółowo. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Korzystanie z punktów przerwania](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Nawigowanie po kodzie w debugerze przy użyciu poleceń kroków

Najczęściej używamy skrótów klawiaturowych w tym miejscu, ponieważ jest to dobry sposób, aby szybko wykonać aplikację w debugerze (równoważne polecenia, takie jak polecenia menu są wyświetlane w nawiasach).

1. Podczas `for` gdy wstrzymane w `Main` pętli w metodzie, naciśnij **F11** (lub wybierz **debugowanie > Step Into)** dwa razy, aby przejść do wywołania `SendMessage` metody.

     Po dwukrotnym naciśnięciu **F11** powinieneś być w tym wierszu kodu:

     `SendMessage(name, a[i]);`

1. Naciśnij **klawisz F11** jeszcze raz, aby wejść do `SendMessage` metody.

     Żółty wskaźnik przechodzi `SendMessage` do metody.

     ![Użyj F11, aby wkroczyć do kodu](../csharp/media/get-started-f11.png "F10 Krok do")

     F11 jest **step into** polecenia i zaliczki wykonywania aplikacji jedną instrukcję naraz. F11 jest dobrym sposobem, aby zbadać przepływ wykonania w najbardziej szczegółowo. (Aby szybciej poruszać się po kodzie, pokazujemy również kilka innych opcji). Domyślnie debuger przeskakuje nad kodem niebędącym użytkownikiem (jeśli chcesz uzyskać więcej szczegółów, zobacz [Tylko mój kod](../../debugger/just-my-code.md)).

     Załóżmy, że skończysz badanie `SendMessage` metody i chcesz wyjść z metody, ale pobyt w debugera. Można to zrobić za pomocą polecenia **Step Out.**

1. Naciśnij **klawisz Shift** + **F11** (lub **Debug > Step Out).**

     To polecenie wznawia wykonywanie aplikacji (i przesuwa debuger) do czasu zwrotu bieżącej metody lub funkcji.

     Powinieneś być z `for` powrotem `Main` w pętli w `SendMessage` metodzie, wstrzymane przy wywołaniu metody.

1. Naciskaj **klawisz F11** kilka razy, aż ponownie powrócisz do wywołania `SendMessage` metody.

1. Podczas gdy wstrzymane przy wywołaniu metody, naciśnij **klawisz F10** (lub wybierz **debugowanie > Step Over)** raz.

     ![Użyj F10, aby przejść przez kod](../csharp/media/get-started-step-over.png "F10 Krok nad")

     Należy zauważyć, tym razem, że debuger nie krok do `SendMessage` metody. **F10** zaliczki debugera bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod nadal wykonuje). Naciskając **F10** `SendMessage` na wywołanie metody (zamiast **F11**), przeskoczyliśmy kod implementacji (który `SendMessage` być może nie jesteśmy zainteresowani w tej chwili). Aby uzyskać więcej informacji na temat różnych sposobów poruszania się po kodzie, zobacz [Nawigowanie po kodzie w debugerze](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Nawigowanie po kodzie za pomocą przycisku Uruchom, aby kliknąć

1. Naciśnij **klawisz F5,** aby ponownie przejść do punktu przerwania.

1. W edytorze kodu przewiń `Console.WriteLine` w dół `SendMessage` i umieść wskaźnik myszy na metodzie w metodzie, aż po lewej stronie pojawi się zielony przycisk **Uruchom, aby kliknąć** ![uruchom.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick (RunToClick)") Etykietka narzędzia dla przycisku pokazuje "Uruchom wykonanie tutaj".

     ![Użyj funkcji Uruchom, aby kliknąć](../csharp/media/get-started-run-to-click.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom, aby kliknąć** jest nowy w [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]pliku . (Jeśli nie widzisz zielonego przycisku strzałki, użyj **F11** w tym przykładzie, aby przejść debuger do właściwego miejsca).

2. Kliknij przycisk **Uruchom, aby kliknąć** ![Uruchom, aby kliknąć](../../debugger/media/dbg-tour-run-to-click.png "RunToClick (RunToClick)").

    Debuger przechodzi do `Console.WriteLine` metody.

    Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. **Uruchom, aby kliknąć** jest przydatna do szybkiego poruszania się w widocznym regionie kodu aplikacji (możesz kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Uruchom ponownie** ![aplikację](../../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5**).

Po naciśnięciu **przycisku Uruchom ponownie**, oszczędza czas w porównaniu do zatrzymania aplikacji i ponownego uruchomienia debugera. Debuger wstrzymuje w pierwszym punkcie przerwania, który jest trafiony przez wykonanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania, który wcześniej ustawiono wewnątrz `for` pętli.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych za pomocą wskazówek dotyczących danych

Funkcje, które umożliwiają sprawdzanie zmiennych są jedną z najbardziej przydatnych funkcji debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu, próbujesz dowiedzieć się, czy zmienne są przechowywanie wartości, które oczekują ich mieć w określonym czasie.

1. Wstrzymane na `name += letters[i]` instrukcji, najedź kursorem na zmienną `letters` i zobaczysz jej wartość domyślną, wartość pierwszego elementu w tablicy, `char[10]`.

1. Rozwiń `letters` zmienną, aby wyświetlić jej właściwości, które zawierają wszystkie elementy, które zawiera zmienna.

1. Następnie umieść wskaźnik `name` myszy na zmiennej, a zobaczysz jej bieżącą wartość, pusty ciąg.

1. Naciśnij **klawisz F5** (lub **Debug** > **Continue)** kilka razy, `for` aby kilka razy iterować przez pętlę, `name` wstrzymując ponownie punkt przerwania i najeżdżając kursorem na zmienną za każdym razem, aby sprawdzić jej wartość.

     ![Wyświetlanie końcówki danych](../csharp/media/get-started-data-tip.gif "Wyświetlanie końcówki danych")

     Wartość zmiennej zmienia się z każdą `for` iteracją pętli, `fr`wyświetlaą `fre`wartości `f`, następnie , a następnie i tak dalej.

     Często podczas debugowania, chcesz szybki sposób, aby sprawdzić wartości właściwości na zmiennych, aby zobaczyć, czy są one przechowywania wartości, które oczekują ich do przechowywania, a wskazówki dotyczące danych są dobrym sposobem, aby to zrobić.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien Autos i Locals

1. Spójrz na okno **Autos** w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go podczas wstrzymania w debugerze, wybierając **debugowanie** > **autos****systemu Windows** > .

    W oknie **Autos** widoczne są zmienne i ich bieżąca wartość. Okno **Autos** zawiera wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (Sprawdź dokumentację zachowania specyficznego dla języka).

1. Następnie spójrz na okno **Zmiennoprawny** na karcie obok okna **Autos.**

1. Rozwiń `letters` zmienną, aby wyświetlić elementy, które zawiera.

     ![Sprawdzanie zmiennych w oknie Dla mieszkańców](../csharp/media/get-started-locals-window.png "Okno miejscowi")

    Okno **Locals** pokazuje zmienne, które znajdują się w bieżącym [zakresie](https://www.wikipedia.org/wiki/Scope_(computer_science)), czyli bieżącego kontekstu wykonywania.

## <a name="set-a-watch"></a>Ustawianie zegarka

1. W oknie głównego edytora kodu `name` kliknij zmienną prawym przyciskiem myszy i wybierz polecenie **Dodaj czujki**.

    Okno **Czujka** zostanie otwarte w dolnej części edytora kodu. Za pomocą okna **Czujka** można określić zmienną (lub wyrażenie), które ma być obserwowane.

    Teraz masz zegarek ustawiony na `name` zmiennej i widać jej zmianę wartości podczas przechodzenia przez debuger. W przeciwieństwie do innych okien zmiennych, **watch** okno zawsze pokazuje zmienne, które obserwujesz (są wyszarzone, gdy poza zakresem).

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

1. Po wstrzymaniu `for` w pętli kliknij okno **Stos wywołań,** które jest domyślnie otwarte w prawym dolnym okienku.

    Jeśli jest zamknięty, otwórz go podczas wstrzymania w debugerze, wybierając **debugowanie** > **stosu wywołań****systemu Windows** > .

2. Kliknij **klawisz F11** kilka razy, aż zobaczysz `SendMessage` pauzę debugera w metodzie. Spójrz na okno **Stos wywołań.**

    ![Sprawdź stos wywołań](../csharp/media/get-started-call-stack.png "BadanieCallStack")

    Okno **Stos wywołań** pokazuje kolejność, w jakiej metody i funkcje są wywoływane. Górna linia pokazuje bieżącą `SendMessage` funkcję (metodę w tej aplikacji). Druga linia pokazuje, że `SendMessage` `Main` został wywołany z metody, i tak dalej.

   > [!NOTE]
   > Okno **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

    Stos wywołań jest dobrym sposobem, aby zbadać i zrozumieć przepływ wykonywania aplikacji.

    Można dwukrotnie kliknąć wiersz kodu, aby przejść do tego kodu źródłowego i który również zmienia bieżący zakres jest sprawdzany przez debugera. Ta akcja nie powoduje przyspieszenia debugera.

    Można również użyć menu prawym przyciskiem myszy z okna **Stos wywołań,** aby wykonać inne czynności. Na przykład można wstawić punkty przerwania do określonych funkcji, przesunąć debuger za pomocą **uruchom do kursora**i przejść do badania kodu źródłowego. Aby uzyskać więcej informacji, zobacz [Jak: Sprawdź stos wywołań](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmienianie przepływu wykonania

1. Naciśnij dwukrotnie **klawisz F11,** aby uruchomić `Console.WriteLine` tę metodę.

1. Gdy debuger został wstrzymany w wywołaniu `SendMessage` metody, użyj myszy, aby pobrać żółtą strzałkę (wskaźnik wykonania) `Console.WriteLine`po lewej stronie i przesunąć żółtą strzałkę w górę o jedną linię, z powrotem do .

1. Naciśnij **klawisz F11**.

    Debuger ponownie przywdzieje `Console.WriteLine` metodę (widać to w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonywania, można wykonać takie czynności, jak testowanie różnych ścieżek wykonywania kodu lub ponownego uruchamiania kodu bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często należy zachować ostrożność przy tej funkcji, a w etykietce narzędzia jest widoczne ostrzeżenie. Mogą pojawić się również inne ostrzeżenia. Przenoszenie wskaźnika nie można przywrócić aplikacji do wcześniejszego stanu aplikacji.

1. Naciśnij **klawisz F5,** aby kontynuować uruchamianie aplikacji.

    Gratulujemy ukończenia tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, krok po kroku kodu i sprawdzić zmienne. Możesz chcieć uzyskać spojrzenie wysokiego poziomu na funkcje debugera wraz z łączami do większej ilości informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
