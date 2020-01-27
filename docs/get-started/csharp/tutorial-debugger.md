---
title: 'Samouczek: debugowanie C# kodu'
description: Dowiedz się, jak uruchomić debuger programu Visual Studio, Przechodź przez kod i sprawdzić dane.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
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
ms.openlocfilehash: 1e19672ccc13b94f93bd21fc02701aa54648199e
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726086"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: Dowiedz się, jak debugowanie C# kodu za pomocą programu Visual Studio

W tym artykule przedstawiono funkcje debugera programu Visual Studio w przewodnik krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [pierwsze spojrzenie na debuger](../../debugger/debugger-feature-tour.md). Gdy użytkownik *debugowanie aplikacji*, zwykle oznacza to, że aplikacja jest uruchamiana w debugerze. Gdy to zrobisz, debuger zapewnia wiele sposobów, aby zobaczyć, co kod robi podczas jego uruchamiania. Można przejść przez kod i przyjrzyj się wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmienić wartości, można zbadać ścieżki wykonywania kodu, czy gałąź kodu nie jest uruchomiona, i tak dalej. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [debugowania dla początkujących](../../debugger/debugging-absolute-beginners.md) przed przejściem w tym artykule.

Mimo że aplikacja demonstracyjna C#, większość funkcji mają zastosowanie do C++, Visual Basic F#, Python, JavaScript i innymi językami obsługiwanymi przez program Visual Studio (F# nie obsługuje Edit-and-continue. F#i język JavaScript nie obsługuje **Autos** okno). Zrzuty ekranu są w języku C#.

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

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **C#** , a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)** . Następnie nadaj nazwę projekt *Get-Started-Debug*.

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

     Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie C# szablonu aplikacji konsolowej (.NET Core)](../../debugger/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź w polu **Nazwa projektu** polecenie *Get-Started-Debug* . Następnie wybierz pozycję **Utwórz**.

   Program Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *program.cs*Zastąp cały kod domyślny przedstawiony tutaj:

    ```csharp
    using System;
    // ...

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    przy użyciu tego kodu:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }

        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

     **F5** uruchamia aplikacji za pomocą debugera dołączony do aplikacji, przetwarzania, ale teraz możemy jeszcze nie wykonano żadnych specjalnych badanie kodu. Dlatego właśnie ładowania aplikacji, a zostaną wyświetlone dane wyjściowe konsoli.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     W tym samouczku utworzymy Przyjrzyj się bliżej aplikacji przy użyciu debugera i pobrać spojrzenie na debugera funkcji.

2. Zatrzymaj debuger, naciskając czerwony przycisk Zatrzymaj ![debugowanie](../../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") przycisku.

3. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomić debuger

1. W `foreach` pętli z `Main` funkcji, ustaw punkt przerwania, klikając w lewy margines następującego kodu:

    `shape.Draw()`

    Pojawi się czerwone kółko, gdzie ustawić punkt przerwania.

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

2. Naciśnij klawisz **F5** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie"), uruchomienie aplikacji, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawiono punkt przerwania.

    ![Ustaw i Traf punkt przerwania](../csharp/media/get-started-set-breakpoint.gif)

    Żółta strzałka reprezentuje instrukcji, w której debuger wstrzymany, również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie jeszcze wykonane).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchomienie debugera i przerywa w pierwszym punkcie przerwania. W przeciwnym razie **F5** będzie nadal działać w aplikacji do następnego punktu przerwania.

    Punkty przerwania są to przydatne, gdy wiadomo, wiersz kodu lub sekcji kodu, który chcesz zbadać szczegółowo.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Przechodzenie do kodu w debugerze, przy użyciu poleceń krokowych

Przede wszystkim, używamy skróty klawiaturowe w tym miejscu, ponieważ jest to dobry sposób, aby uzyskać szybkie na wykonywanie aplikacji w debugerze (równoważne polecenia takie jak menu poleceń są wyświetlane w nawiasach).

1. Podczas wstrzymania w `shape.Draw` metody wywołania w `Main` metody, naciśnij klawisz **F11** (lub wybierz **debugowania > Step Into**) aby przejść do kodu dla `Rectangle` klasy.

     ![Użyj klawisza F11, aby przejść do kodu](../csharp/media/get-started-f11.png "F11 Wkrocz do")

     Jest F11 **Step Into** poleceń i prowadzi aplikacji wykonanie jednej instrukcji w danym momencie. F11 jest dobrym sposobem na zbadanie przepływ wykonania w najbardziej szczegółowy. (Aby szybciej przejść przez kod, pokazujemy inne opcje.) Domyślnie debuger pomija kod niebędący użytkownikiem (Aby uzyskać więcej szczegółów, zobacz [tylko mój kod](../../debugger/just-my-code.md)).

2. Naciśnij klawisz **F10** (lub wybierz **Debuguj > Step Over**) kilka razy dopóki debuger zatrzymuje się na `base.Draw` wywołania metody, a następnie klawisz **F10** jeszcze raz.

     ![Użyj klawisza F10, aby przekroczyć kod](../csharp/media/get-started-step-over.png "F10 krok po kroku")

     Zauważ teraz, że debuger nie wkracza w `Draw` metody klasy bazowej (`Shape`). **F10** wyjście z kodu bez przechodzenie krok po kroku do funkcji lub metody w kodzie aplikacji (nadal wykonuje kod). Naciskając klawisz **F10** w wywołaniu metody `base.Draw` (zamiast **F11**), pominięto kod implementacji dla `base.Draw` (co może nie interesuje Cię teraz).

## <a name="navigate-code-using-run-to-click"></a>Przechodzenie do kodu przy użyciu polecenia Uruchom do kliknięcia

1. Kliknij prawym przyciskiem myszy ustawiony wcześniej punkt przerwania i wybierz polecenie **Usuń punkt przerwania** (lub naciśnij klawisz **Ctrl** + **SHIFT** + **F9** , aby usunąć wszystkie punkty przerwania).

1. W edytorze kodu przewiń w dół i umieść kursor nad metodą `Console.WriteLine` w klasie `Triangle` do momentu, gdy zielony przycisk **Uruchom** do ![kliknięcia zostanie wyświetlony](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") po lewej stronie. Etykietka narzędzia dla przycisku pokazuje "uruchom wykonywanie do tego miejsca".

     ![Korzystanie z funkcji uruchamiania do kliknięcia](../csharp/media/get-started-run-to-click.png "Uruchom do kliknięcia")

   > [!NOTE]
   > **Uruchamianie do kliknięcia** przycisk jest nowego w programie [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Jeśli nie widzisz przycisku zieloną strzałkę, użyj **F11** w tym przykładzie zamiast Aby awansować debugera we właściwym miejscu.

2. Kliknij przycisk **Uruchom, aby kliknąć** polecenie ![Uruchom, aby kliknąć](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Za pomocą tego przycisku jest podobna do ustawienia tymczasowy punkt przerwania. **Uruchamianie do kliknięcia** jest przydatna do poruszania się szybko w obrębie regionu widoczne dla kodu aplikacji (możesz kliknąć dowolny otwarty plik).

    Przejście do debugera `Console.WriteLine` implementacji metody dla `Triangle` klasy. (Jeśli debuger wstrzymuje się w pierwszej kolejności w punkcie przerwania, który został ustawiony wcześniej, należy ponownie **kliknąć polecenie Uruchom** , aby przejść do debugera, aby `Console.WriteLine`).

    Podczas wstrzymania, zauważysz błąd pisowni! Dane wyjściowe "Rysowanie trangle" jest błędnie wpisana. Będziemy mogli ją naprawić miejscu podczas uruchamiania aplikacji w debugerze.

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

1. Klikaj "Rysowanie trangle", a następnie wpisz korekty, zmiana "trangle" na "trójkąt".

1. Naciśnij klawisz **F11** raz i możesz zobaczyć ponownie przejście debugera.

    > [!NOTE]
    > W zależności od tego, jakiego typu kod edytowany w debugerze może zostać wyświetlony komunikat ostrzegawczy. W niektórych scenariuszach kod należy ponownie skompilować, zanim będzie można kontynuować.

## <a name="step-out"></a>Wyjdź

Załóżmy, że wszystko będzie gotowe badanie `Draw` method in Class metoda `Triangle` klasy i, o których chcesz uzyskiwać dostęp do najważniejszych funkcji, ale pozostanie w debugerze. Można to zrobić za pomocą **Step Out** polecenia.

1. Naciśnij klawisz **Shift** + **F11** (lub **Debuguj > Wyjdź**).

     To polecenie wznawia działanie aplikacji (i umożliwia przejście do) do momentu zwraca bieżącą funkcję.

     Powinien nastąpić powrót `foreach` pętli w `Main` metody. Jeśli nie, naciśnij klawisz **Shift** + **F11** po raz drugi.

1. Kliknij przycisk na lewym marginesie, aby dodać nowy punkt przerwania w pętli `for`.

## <a name="restart-your-app-quickly"></a>Szybko Uruchom ponownie swoją aplikację

Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**).

Po naciśnięciu klawisza **ponowne uruchomienie**, można zaoszczędzić czas i zatrzymywanie aplikacji oraz ponownego uruchamiania debugera. Debuger wstrzymuje na pierwszy punkt przerwania zostanie osiągnięty przez wykonywanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania, możesz ustawić na `shape.Draw()` metody.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych z poradami do danych

Funkcje, które pozwalają na sprawdzanie zmiennych są jednymi z najbardziej przydatnych funkcjach debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz sprawdzić, czy zmienne są przechowywane wartości, których można oczekiwać, aby użytkownicy posiadali w danym momencie.

1. Gdy wstrzymana na `shape.Draw()` metodę, umieść kursor nad `shape` obiektu i zobacz jego domyślne wartości właściwości, typ obiektu `Rectangle`.

1. Rozwiń `shape` obiektu, aby wyświetlić jego właściwości, takie jak `Height` właściwość, która ma wartość 0.

1. Naciśnij klawisz **F10** (lub **debugowania** > **Step Over**) kilka razy do iterowania po raz `foreach` pętli, wstrzymywanie ponownie na `shape.Draw()`.

1. Najedź kursorem na obiekcie Shapes, ponownie i tym razem zostanie wyświetlony, masz nowy obiekt o typie `Triangle`.

     ![Wyświetlanie etykietki danych](../csharp/media/get-started-data-tip.gif "Wyświetlanie etykietki danych")

    Często podczas debugowania, chcesz, aby szybko sprawdzić wartości zmiennych, aby zobaczyć, czy będą one przechowywane wartości, których oczekujesz, aby przechowywać, właściwości i porady dotyczące danych są dobrym sposobem, aby to zrobić.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Przyjrzyj się **Autos** okna w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go podczas wstrzymaniu w debugerze, wybierając **debugowania** > **Windows** > **Autos**.

1. Rozwiń `shapes` obiektu.

     ![Sprawdź zmienne w oknie Autokorekty](../csharp/media/get-started-autos-window.png "Okno Autokorekty")

    W **Autos** oknie zostanie wyświetlony, zmienne i ich bieżącą wartość. **Autos** okno pokazuje wszystkie zmienne używane w bieżącym wierszu lub poprzedni wiersz (zobacz dokumentację dla zachowania specyficzne dla języka).

1. Następnie Przyjrzyj się **lokalne** okna, na karcie obok **automatyczne** okna.

    **Lokalne** okno zawiera zmienne, które znajdują się w bieżącej [zakres](https://www.wikipedia.org/wiki/Scope_(computer_science)), oznacza to, że bieżący kontekst wykonywania.

## <a name="set-a-watch"></a>Ustawianie wyrażenia kontrolnego

1. W oknie edytora głównego kodu, kliknij prawym przyciskiem myszy `shapes` obiektu, a następnie wybierz **Dodaj czujkę**.

    **Obejrzyj** zostanie otwarte okno w dolnej części edytora kodu. Możesz użyć **Obejrzyj** okna, aby określić zmienną (lub wyrażenie), który chcesz śledzić na.

    Teraz masz wyrażenia kontrolnego nastavit `shapes` obiektu, aby sprawdzić jej wartość zmienić podczas przeglądania przez debuger. W przeciwieństwie do innych zmiennych systemu windows **Obejrzyj** okno zawsze zawiera zmienne, obserwujesz (są one wygaszone się kiedy poza zakresem).

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

1. Gdy został wstrzymany w `foreach` pętli, kliknij przycisk **stos wywołań** okno, które jest domyślnie otwarty w dolnym okienku po prawej stronie.

    Jeśli jest zamknięty, otwórz go podczas wstrzymaniu w debugerze, wybierając **debugowania** > **Windows** > **stos wywołań**.

2. Kliknij przycisk **F11** kilka razy, aż zostanie wyświetlony debugera wstrzymywania w `Base.Draw` metodę `Triangle` klasy w edytorze kodu. Przyjrzyj się **stos wywołań** okna.

    ![Badanie stosu wywołań](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    **Stos wywołań** okno pokazuje kolejność, w którym są wprowadzenie wywoływane metody i funkcje. Górny wiersz zawiera bieżącą funkcję ( `Triangle.Draw` metody w tej aplikacji). Drugi wiersz wskazuje, że `Triangle.Draw` została wywołana z `Main` metoda i tak dalej.

   > [!NOTE]
   > **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

    Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przyjrzeć się kodu źródłowego i zmienia także bieżący zakres kontrolowanym przez debuger. Ta akcja nie wcześniejsze debugera.

    Można również użyć menu kliknij prawym przyciskiem myszy **stos wywołań** okna, aby wykonywać inne czynności. Na przykład, wstawianie punktów przerwania do określonych funkcji, przejdź do debugera przy użyciu **Uruchom do kursora**i przejdź zbadanie kodu źródłowego. Aby uzyskać więcej informacji, zobacz [jak: Sprawdź stos wywołań](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

1. Za pomocą debugera został wstrzymany w `Circle.Draw` wywołania metody za pomocą myszy Pobierz żółta strzałka (wskaźnik wykonania) po lewej stronie, a żółta strzałka w górę o jeden wiersz, aby przenieść `Console.WriteLine` wywołania metody.

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
