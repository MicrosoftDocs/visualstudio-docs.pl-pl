---
title: 'Samouczek: Debugowanie kodu Visual Basic'
description: Dowiedz się, jak uruchomić debuger programu Visual Studio, Przechodź przez kod i sprawdzić dane.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eb7ac3dacf5d572a13eadf8a37b194962b2ef49
ms.sourcegitcommit: 4a4eed115525c6d34a1fbdf87b793893cd43b70d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "77001487"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Samouczek: uczenie się debugowania kodu Visual Basic za pomocą programu Visual Studio

W tym artykule przedstawiono funkcje debugera programu Visual Studio w przewodnik krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Gdy użytkownik *debugowanie aplikacji*, zwykle oznacza to, że aplikacja jest uruchamiana w debugerze. Gdy to zrobisz, debuger zapewnia wiele sposobów, aby zobaczyć, co kod robi podczas jego uruchamiania. Można przejść przez kod i przyjrzyj się wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmienić wartości, można zbadać ścieżki wykonywania kodu, czy gałąź kodu nie jest uruchomiona, i tak dalej. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [debugowania dla początkujących](../../debugger/debugging-absolute-beginners.md) przed przejściem w tym artykule.

Mimo że C#aplikacja demonstracyjna jest Visual Basic, większość funkcji ma zastosowanie do języków, C++, F#, Python, JavaScript i innych obsługiwanych przez program Visual Studio (F# nie obsługuje funkcji Edit-and-Continue. F#i język JavaScript nie obsługuje **Autos** okno). Zrzuty ekranu znajdują się w Visual Basic.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i identyfikować punkty przerwania.
> * Dowiedz się więcej poleceń, aby przejść przez kod w debugerze
> * Sprawdzanie zmiennych w oknach debugera i porady dotyczące danych
> * Sprawdź stos wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany program Visual Studio 2019 i **Międzyplatformowe obciążenie dla programu .NET Core** .

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany program Visual Studio 2017 i **Międzyplatformowe obciążenie dla programu .NET Core** .

::: moniker-end

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsolowej .NET Core. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)** . Następnie nadaj nazwę projekt *Get-Started-Debug*.

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

     Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie szablonu Visual Basic dla aplikacji konsolowej (.NET Core)](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź w polu **Nazwa projektu** polecenie *Get-Started-Debug* . Następnie wybierz pozycję **Utwórz**.

   Program Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *programie program. vb*zamiast tego Zastąp cały kod domyślny następującym kodem:

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

1. Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

     **F5** uruchamia aplikacji za pomocą debugera dołączony do aplikacji, przetwarzania, ale teraz możemy jeszcze nie wykonano żadnych specjalnych badanie kodu. Dlatego właśnie ładowania aplikacji, a zostaną wyświetlone dane wyjściowe konsoli.

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

2. Zatrzymaj debuger, naciskając czerwony przycisk Zatrzymaj ![debugowanie](../../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") (**SHIFT** + **F5**).

3. W oknie konsoli naciśnij klawisz, aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomić debuger

1. W `For` pętli z `Main` funkcji, ustaw punkt przerwania, klikając w lewy margines następującego kodu:

    `name += letters(i)`

    W miejscu ustawionym na ![punkt przerwania pojawia się](../../debugger/media/dbg-breakpoint.png "Punkt przerwania") czerwony okrąg.

    Punkty przerwania są jedną z najważniejszych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

2. Naciśnij klawisz **F5** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie"), uruchomienie aplikacji, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawiono punkt przerwania.

    ![Ustaw i Traf punkt przerwania](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Żółta strzałka reprezentuje instrukcji, w której debuger wstrzymany, również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie jeszcze wykonane).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchomienie debugera i przerywa w pierwszym punkcie przerwania. W przeciwnym razie **F5** będzie nadal działać w aplikacji do następnego punktu przerwania.

    Punkty przerwania są to przydatne, gdy wiadomo, wiersz kodu lub sekcji kodu, który chcesz zbadać szczegółowo. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Używanie punktów przerwania](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Przechodzenie do kodu w debugerze, przy użyciu poleceń krokowych

Przede wszystkim, używamy skróty klawiaturowe w tym miejscu, ponieważ jest to dobry sposób, aby uzyskać szybkie na wykonywanie aplikacji w debugerze (równoważne polecenia takie jak menu poleceń są wyświetlane w nawiasach).

1. Gdy jest wstrzymana w pętli `For` w metodzie `Main`, naciśnij klawisz **F11** (lub wybierz polecenie **Debuguj > Wkrocz**) dwa razy, aby przejść do wywołania metody `SendMessage`.

     Po dwukrotnym naciśnięciu klawisza **F11** należy mieć następujący wiersz kodu:

     `SendMessage(name, a(i))`

1. Naciśnij klawisz **F11** jeszcze raz, aby przejść do metody `SendMessage`.

     Żółty wskaźnik jest zaawansowany do metody `SendMessage`.

     ![Użyj klawisza F11, aby przejść do kodu](../visual-basic/media/get-started-f11-vb.png "Wkrocz do kroku")

     Jest F11 **Step Into** poleceń i prowadzi aplikacji wykonanie jednej instrukcji w danym momencie. F11 jest dobrym sposobem na zbadanie przepływ wykonania w najbardziej szczegółowy. (Aby szybciej przejść przez kod, pokazujemy inne opcje.) Domyślnie debuger pomija kod niebędący użytkownikiem (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../../debugger/just-my-code.md)).

     Załóżmy, że skończysz badanie metody `SendMessage` i chcesz uzyskać dostęp do metody, ale pozostać w debugerze. Można to zrobić za pomocą **Step Out** polecenia.

1. Naciśnij klawisz **Shift** + **F11** (lub **Debuguj > Wyjdź**).

     To polecenie wznawia wykonywanie aplikacji (i zwiększa debuger) do momentu, gdy bieżąca metoda lub funkcja zwróci wynik.

     Należy wrócić do pętli `For` w metodzie `Main`, wstrzymane w wywołaniu metody `SendMessage`.

1. Naciśnij klawisz **F11** , aby ponownie wrócić do metody `SendMessage`.

1. Po wstrzymaniu wywołania metody naciśnij klawisz **F10** (lub wybierz polecenie **Debuguj > krok więcej**).

     ![Użyj klawisza F10, aby przekroczyć kod](../visual-basic/media/get-started-step-over-vb.png "F10 krok po kroku")

     Zauważ, że debuger nie przekroczy metody `SendMessage`. **F10** wyjście z kodu bez przechodzenie krok po kroku do funkcji lub metody w kodzie aplikacji (nadal wykonuje kod). Naciskając klawisz **F10** w wywołaniu metody `SendMessage` (zamiast **F11**), pominięto kod implementacji dla `SendMessage` (co może nie interesuje Cię teraz). Aby uzyskać więcej informacji na temat różnych sposobów poruszania się po kodzie, zobacz [nawigowanie po kodzie w debugerze](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Przechodzenie do kodu przy użyciu polecenia Uruchom do kliknięcia

1. W edytorze kodu przewiń w dół i umieść kursor nad metodą `Console.WriteLine` w komunikacie `SendMessage` do momentu, gdy zielony przycisk Uruchom ![do kliknięcia zostanie wyświetlony po](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") lewej stronie. Etykietka narzędzia dla przycisku pokazuje "uruchom wykonywanie do tego miejsca".

     ![Korzystanie z funkcji uruchamiania do kliknięcia](../visual-basic/media/get-started-run-to-click-vb.png "Uruchom do kliknięcia")

   > [!NOTE]
   > **Uruchamianie do kliknięcia** przycisk jest nowego w programie [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. (Jeśli nie widzisz przycisku Zielona strzałka, użyj klawisza **F11** w tym przykładzie zamiast, aby przejść do odpowiedniego miejsca w debugerze).

2. Kliknij przycisk **Uruchom, aby kliknąć** polecenie ![Uruchom, aby kliknąć](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger przechodzi do metody `Console.WriteLine`.

    Za pomocą tego przycisku jest podobna do ustawienia tymczasowy punkt przerwania. **Uruchamianie do kliknięcia** jest przydatna do poruszania się szybko w obrębie regionu widoczne dla kodu aplikacji (możesz kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybko Uruchom ponownie swoją aplikację

Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**).

Po naciśnięciu klawisza **ponowne uruchomienie**, można zaoszczędzić czas i zatrzymywanie aplikacji oraz ponownego uruchamiania debugera. Debuger wstrzymuje na pierwszy punkt przerwania zostanie osiągnięty przez wykonywanie kodu.

Debuger zatrzyma się ponownie w punkcie przerwania, który został wcześniej ustawiony wewnątrz pętli `For`.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych z poradami do danych

Funkcje, które pozwalają na sprawdzanie zmiennych są jednymi z najbardziej przydatnych funkcjach debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz sprawdzić, czy zmienne są przechowywane wartości, których można oczekiwać, aby użytkownicy posiadali w danym momencie.

1. Gdy jest wstrzymana w instrukcji `name += letters[i]`, umieść wskaźnik myszy na zmiennej `letters` i zobaczysz jej wartość domyślną, wartość pierwszego elementu w tablicy, `"f"c`.

1. Następnie umieść wskaźnik myszy nad zmienną `name` i zobaczysz jej bieżącą wartość jako pusty ciąg.

1. Naciśnij klawisz **F5** (lub **Debuguj** > **Kontynuuj**) kilka razy, aby wielokrotnie powtarzać kilka razy przez pętlę `For`, zatrzymując ponownie w punkcie przerwania i umieszczając wskaźnik myszy na zmiennej `name` za każdym razem, aby sprawdzić jej wartość.

     ![Wyświetlanie etykietki danych](../visual-basic/media/get-started-data-tip-vb.png "Wyświetlanie etykietki danych")

     Wartość zmiennej zmienia się z każdą iteracją `For` pętli, wyświetlając wartości `f`, następnie `fr`, a następnie `fre`i tak dalej.

     Często podczas debugowania, chcesz, aby szybko sprawdzić wartości zmiennych, aby zobaczyć, czy będą one przechowywane wartości, których oczekujesz, aby przechowywać, właściwości i porady dotyczące danych są dobrym sposobem, aby to zrobić.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Przyjrzyj się **Autos** okna w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go podczas wstrzymaniu w debugerze, wybierając **debugowania** > **Windows** > **Autos**.

    W **Autos** oknie zostanie wyświetlony, zmienne i ich bieżącą wartość. **Autos** okno pokazuje wszystkie zmienne używane w bieżącym wierszu lub poprzedni wiersz (zobacz dokumentację dla zachowania specyficzne dla języka).

1. Następnie Przyjrzyj się **lokalne** okna, na karcie obok **automatyczne** okna.

1. Rozwiń zmienną `letters`, aby wyświetlić elementy, które zawiera.

     ![Sprawdź zmienne w oknie zmiennych lokalnych](../visual-basic/media/get-started-locals-window-vb.png "Okno zmiennych lokalnych")

    **Lokalne** okno zawiera zmienne, które znajdują się w bieżącej [zakres](https://www.wikipedia.org/wiki/Scope_(computer_science)), oznacza to, że bieżący kontekst wykonywania.

## <a name="set-a-watch"></a>Ustawianie wyrażenia kontrolnego

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy zmienną `name` i wybierz polecenie **Dodaj czujkę**.

    **Obejrzyj** zostanie otwarte okno w dolnej części edytora kodu. Możesz użyć **Obejrzyj** okna, aby określić zmienną (lub wyrażenie), który chcesz śledzić na.

    Teraz masz ustawiony czujkę na zmiennej `name` i zobaczysz jej zmianę wartości podczas przechodzenia przez debuger. W przeciwieństwie do innych zmiennych systemu windows **Obejrzyj** okno zawsze zawiera zmienne, obserwujesz (są one wygaszone się kiedy poza zakresem).

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

1. Gdy został wstrzymany w `For` pętli, kliknij przycisk **stos wywołań** okno, które jest domyślnie otwarty w dolnym okienku po prawej stronie.

    Jeśli jest zamknięty, otwórz go podczas wstrzymaniu w debugerze, wybierając **debugowania** > **Windows** > **stos wywołań**.

2. Klikaj polecenie **F11** kilka razy, aż zobaczysz debuger pauzy w metodzie `SendMessage`. Przyjrzyj się **stos wywołań** okna.

    ![Badanie stosu wywołań](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    **Stos wywołań** okno pokazuje kolejność, w którym są wprowadzenie wywoływane metody i funkcje. Górny wiersz zawiera bieżącą funkcję ( `SendMessage` metody w tej aplikacji). Drugi wiersz wskazuje, że `SendMessage` została wywołana z `Main` metoda i tak dalej.

   > [!NOTE]
   > **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

    Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przyjrzeć się kodu źródłowego i zmienia także bieżący zakres kontrolowanym przez debuger. Ta akcja nie wcześniejsze debugera.

    Można również użyć menu kliknij prawym przyciskiem myszy **stos wywołań** okna, aby wykonywać inne czynności. Na przykład, wstawianie punktów przerwania do określonych funkcji, przejdź do debugera przy użyciu **Uruchom do kursora**i przejdź zbadanie kodu źródłowego. Aby uzyskać więcej informacji, zobacz [jak: Sprawdź stos wywołań](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

1. Naciśnij dwukrotnie klawisz **F11** , aby uruchomić metodę `Console.WriteLine`.

1. Po wstrzymaniu debugera w wywołaniu metody `SendMessage` Użyj myszy, aby uzyskać żółtą strzałkę (wskaźnik wykonywania) po lewej stronie, a następnie przesuń żółtą strzałkę w górę o jeden wiersz w górę, z powrotem do `Console.WriteLine`.

1. Naciśnij klawisz **F11**.

    Debuger umożliwia ponowne wykonanie `Console.WriteLine` — metoda (się dzieje w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonania, można wykonać czynności, jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często muszą być ostrożnym z tej funkcji, a następnie zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

1. Naciśnij klawisz **F5** ma kontynuować wykonywanie aplikacji.

    Gratulujemy wykonanie kroków tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
