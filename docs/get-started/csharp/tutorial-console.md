---
title: 'Samouczek: tworzenie prostej aplikacji konsolowej w języku C# '
description: Dowiedz się, jak utworzyć aplikację konsolową w języku C# Visual Studio, krok po kroku.
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 20732b0d7fb09de6079b0c1b7b06d2ae89802a5b
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649181"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>Samouczek: tworzenie prostej aplikacji konsolowej C# w Visual Studio (część 1 z 2)

W tym samouczku użyjesz usługi Visual Studio do utworzenia i uruchomienia aplikacji konsolowej języka C# oraz poznasz niektóre funkcje zintegrowanego środowiska projektowego (IDE) środowiska Visual Studio, gdy to zrobisz. Ten samouczek jest częścią 1 dwusekwowej serii samouczków.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Utwórz Visual Studio projektu.
> * Utwórz aplikację konsoli w języku C#.
> * Debuguj aplikację.
> * Zamknij aplikację.
> * Sprawdź pełny kod.

[W części 2](tutorial-console-part-2.md)rozszerzysz tę aplikację o dodatkowe projekty, wskazówki dotyczące debugowania i pakiety innych firm.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz mieć Visual Studio zainstalowane.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzymy projekt aplikacji w języku C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Nowy** plik  >    >  **Project**.
   (Ewentualnie naciśnij klawisze **Ctrl** + **Shift (Przesunięcie)** + **N**).

3. W lewym okienku okna dialogowego **Nowy Project** rozwiń pozycję **C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj plikowi **_nazwę Calculator_**.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Project w Visual Studio IDE](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu Aplikacja konsolowa **(.NET Core),** możesz go pobrać, dodając obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.** Oto jak to zrobić.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1. Użyj okna dialogowego Project Nowy

1. Wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna **dialogowego Project** nowy.

   ![Wybierz link Open Instalator programu Visual Studio (Otwórz Project) w oknie dialogowym New Project (Nowe okno dialogowe)](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

   ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu Narzędzia

1. Anuluj poza oknie **dialogowym Project** i z górnego paska menu wybierz pozycję **Narzędzia** Pobierz narzędzia > **i funkcje.**

1. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **C#** z listy Język. Następnie wybierz **Windows** z listy Platform (Platforma) i **Console (Konsola)** z listy typów projektów. 

   Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa,** a następnie wybierz pozycję **Dalej.**

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Wybierz szablon języka C# dla aplikacji konsolowej (.NET Framework)":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa,** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w chmurze Instalator programu Visual Studio obciążenie Tworzenie aplikacji dla wielu platform dla **platformy .NET Core.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub *wprowadź* **calculator w Project nazwy** projektu. Następnie wybierz pozycję **Dalej.**

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="W oknie &quot;Konfigurowanie nowego projektu&quot; nadaj projektowi nazwę &quot;Calculator&quot;":::
   
1. W **oknie Dodatkowe informacje** dla struktury docelowej należy już wybrać platformę **.NET Core 3.1.** Jeśli nie, wybierz **pozycję .NET Core 3.1.** Następnie wybierz pozycję **Utwórz**.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1":::

   Visual Studio nowy projekt, który zawiera domyślny kod "Hello world".

::: moniker-end

## <a name="create-the-app"></a>Tworzenie aplikacji

Najpierw poznamy podstawową matematykę liczb całkowitych w języku C#. Następnie dodamy kod, aby utworzyć podstawowy kalkulator. Następnie będziemy debugować aplikację, aby znaleźć i naprawić błędy. Na koniec uściślimy kod, aby był bardziej wydajny.

### <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Zacznijmy od podstawowych obliczeń matematycznych na liczbach całkowitych w języku C#.

1. W edytorze kodu usuń domyślny kod "Hello world".

    ![Usuń domyślny kod Hello world z nowej aplikacji kalkulatora](./media/csharp-console-calculator-deletehelloworld.png)

   W szczególności usuń wiersz , który mówi `Console.WriteLine("Hello World!");` .

1. W jego miejscu wpisz następujący kod:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Zwróć uwagę, że gdy to zrobisz, funkcja IntelliSense w Visual Studio oferuje opcję autouzupełniania wpisu.

    > [!NOTE]
    > Następująca animacja nie ma na celu zduplikowania poprzedniego kodu. Ma on na celu tylko pokazanie, jak działa funkcja autouzupełniania.

    ![Animacja kodu matematycznych liczb całkowitych, która pokazuje funkcję autouzupełniania IntelliSense w Visual Studio IDE](./media/integer-math-intellisense.gif)

1. Wybierz zielony przycisk **Start obok** opcji **Kalkulator,** aby skompilować i uruchomić program, lub naciśnij **klawisz F5.**

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację na pasku narzędzi](./media/csharp-console-calculator-button.png)

   Zostanie otwarte okno konsoli, które pokazuje sumę 42 + 119, czyli **161**.

    ![Okno konsoli z wynikami obliczeń matematycznych na liczbach całkowitych](./media/csharp-console-integer-math.png)

1. **(Opcjonalnie)** Możesz zmienić operator , aby zmienić wynik. Na przykład można zmienić operator w wierszu kodu na dla odejmowania, mnożenia `+` `int c = a + b;` lub `-` `*` `/` dzielenia. Następnie po uruchomieniu programu wynik również się zmieni.

1. Zamknij okno konsoli.

### <a name="add-code-to-create-a-calculator"></a>Dodawanie kodu w celu utworzenia kalkulatora

Kontynuujmy, dodając do projektu bardziej złożony zestaw kodu kalkulatora.

1. Usuń cały kod wyświetlony w edytorze kodu.

1. Wprowadź lub wklej następujący nowy kod w edytorze kodu:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Wybierz **pozycję Kalkulator,** aby uruchomić program, lub naciśnij **klawisz F5.**

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację na pasku narzędzi](./media/csharp-console-calculator-button.png)

   Zostanie otwarte okno konsoli.

1. Wyświetl aplikację w oknie konsoli, a następnie postępuj zgodnie z monitami, aby dodać numery **42** i **119.**

   Aplikacja powinna wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z wyświetloną aplikacją Kalkulator i monitami o akcje do podjęcia](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Dodawanie funkcji do kalkulatora

Dostosujmy kod, aby dodać kolejne funkcje.

### <a name="add-decimals"></a>Dodawanie miejsc dziesiętnych

Aplikacja kalkulatora obecnie akceptuje i zwraca liczby pełne. Będzie to jednak bardziej precyzyjne, jeśli dodamy kod, który umożliwia korzystanie z miejsc dziesiętnych.

Tak jak na poniższym zrzucie ekranu, jeśli po uruchomieniu aplikacji podzielisz liczbę 42 przez liczbę 119, wynik będzie następujący: 0 (zero), co nie jest dokładne.

![Okno konsoli przedstawiające aplikację Kalkulator, która nie zwraca liczby dziesiętnej w wyniku](./media/csharp-console-calculator-nodecimal.png)

Naprawmy kod tak, aby obsługiwali miejsca dziesiętne.

1. Naciśnij **klawisz Ctrl**  +  **H,** aby otworzyć **kontrolkę Znajdź i zamień.**

1. Zmień każde wystąpienie `int` zmiennej na `float` .

   Upewnij się, że przełączasz klawisze **Match case** **(Alt** C) i Match whole word (Alt W ) w kontrolce + Znajdź i   +  **zamień.**

    ![Animacja kontrolki Znajdź i zamień przedstawiająca sposób zmiany zmiennej int na zmienną zmiennoprzecinkową](./media/find-replace-control-animation.gif)

1. Uruchom ponownie aplikację kalkulatora i podziel liczbę **42** przez liczbę **119**.

   Zwróć uwagę, że aplikacja zwraca teraz liczbę dziesiętną zamiast zera.

    ![Okno konsoli z wyświetloną aplikacją Kalkulator, która teraz zwraca liczbę dziesiętną](./media/csharp-console-calculator-decimal.png)

Jednak aplikacja generuje tylko wynik dziesiętny. Dokonajmy kilku kolejnych dostrojeń w kodzie, aby aplikacja również potrafiła obliczać liczby dziesiętne.

1. Użyj **kontrolki Znajdź i zamień** **(Ctrl**  +  **H),** aby zmienić każde wystąpienie zmiennej na , i , aby zmienić każde wystąpienie `float` metody na `double` `Convert.ToInt32` `Convert.ToDouble` .

1. Uruchom aplikację kalkulatora i podziel liczbę **42,5** przez **liczbę 119,75.**

   Zwróć uwagę, że aplikacja akceptuje teraz wartości dziesiętne i zwraca dłuższą liczbę dziesiętną jako wynik.

    ![Okno konsoli przedstawiające aplikację Kalkulator, która teraz akceptuje liczby dziesiętne i w wyniku zwraca dłuższą liczbę dziesiętną](./media/csharp-console-calculator-usedecimals.png)

    (Naprawimy liczbę miejsc dziesiętnych w sekcji [Poprawianie](#revise-the-code) kodu).

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ulepszyliśmy naszą podstawową aplikację kalkulatora, ale nie ma ona jeszcze bezpiecznych aplikacji do obsługi wyjątków, takich jak błędy danych wejściowych użytkownika.

Jeśli na przykład spróbujesz podzielić liczbę przez zero lub wprowadzić znak alfa, gdy aplikacja oczekuje znaku liczbowego (lub odwrotnie), aplikacja może przestać działać, zwrócić błąd lub zwrócić nieoczekiwany wynik nieliczbowy.

Przejdźmy przez kilka typowych błędów wejściowych użytkownika, znajdźmy je w debugerze, jeśli się tam pojawią, i naprawmy je w kodzie.

> [!TIP]
> Aby uzyskać więcej informacji na temat debugera i sposobu jego działania, zobacz pierwsze spojrzenie na Visual Studio [debugera.](../../debugger/debugger-feature-tour.md)

### <a name="fix-the-divide-by-zero-error"></a>Naprawienie błędu "podziel przez zero"

Próba podzielenia liczby przez zero może spowodować zablokowanie aplikacji konsolowej, a następnie pokazanie, co jest nie tak w edytorze kodu.

   ![Zrzut ekranu przedstawiający Visual Studio kodu pokazujący wiersz wyróżniony kolorem żółtym i błąd Nieobsługiwany wyjątek dla błędu "Próba podzielenia przez zero".](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Czasami aplikacja nie zawiesza się, a debuger nie wyświetla błędu dzielenia przez zero. Zamiast tego aplikacja może zwrócić nieoczekiwany wynik nieliczbowy, taki jak symbol nieskończoności. Nadal obowiązuje następująca poprawka kodu.

Zmieńmy kod, aby obsłużyć ten błąd.

1. Usuń kod wyświetlany bezpośrednio między i `case "d":` komentarzem z komunikatem `// Wait for the user to respond before closing` .

1. Zastąp go następującym kodem:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Po dodaniu kodu sekcja z instrukcji powinna `switch` wyglądać podobnie do poniższego zrzutu ekranu:

   ![Poprawiona sekcja "switch" w edytorze Visual Studio kodu](./media/csharp-console-calculator-switch-code.png)

Teraz, gdy podzielisz dowolną liczbę przez zero, aplikacja poprosi o kolejną liczbę. Jeszcze lepiej: nie przestanie pytać, dopóki nie podano liczby innej niż zero.

   ![Zrzut ekranu Visual Studio kodu pokazujący kod instrukcji switch z sprawdzeniem wpisu dodanego dzielnia o wartości spoza zera.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Naprawienie błędu "format"

Jeśli po wprowadzeniu znaku alfa aplikacja oczekuje znaku numerycznego (lub odwrotnie), aplikacja konsolowa zawiesza się. Visual Studio następnie pokazuje, co jest nie tak w edytorze kodu.

   ![W Visual Studio kodu wyświetlany jest błąd formatu](./media/csharp-console-calculator-format-error.png)

Aby naprawić ten błąd, musimy refaktoryzować wprowadzony wcześniej kod.

#### <a name="revise-the-code"></a>Poprawianie kodu

Zamiast polegać na klasie do obsługi całego kodu, podzielimy naszą aplikację `program` na dwie klasy: `Calculator` i `Program` .

Klasa będzie obsługiwać większość pracy obliczeniowej, a klasa będzie obsługiwać interfejs użytkownika i pracę `Calculator` `Program` przechwytywania błędów.

Zaczynajmy.

1. Usuń wszystko w przestrzeni `Calculator` nazw między otwierającym i zamykającym nawiasem klamrowy:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Następnie dodaj nową `Calculator` klasę w następujący sposób:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Następnie dodaj nową  `Program` klasę w następujący sposób:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Wybierz **pozycję Kalkulator,** aby uruchomić program, lub naciśnij **klawisz F5.**

1. Postępuj zgodnie z monitami i podziel liczbę **42** przez liczbę **119**. Aplikacja powinna wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli przedstawiające refaktozowana aplikacja Kalkulator, która zawiera monity dotyczące akcji do podjęcia i obsługi błędów w przypadku nieprawidłowych danych wejściowych](./media/csharp-console-calculator-refactored.png)

    Zwróć uwagę, że możesz wprowadzać więcej równań, dopóki nie zdecydujesz się zamknąć aplikacji konsolowej. Zmniejszyliśmy również liczbę miejsc dziesiętnych w wyniku.

## <a name="close-the-app"></a>Zamykanie aplikacji

1. Jeśli jeszcze tego nie zrobiono, zamknij aplikację kalkulatora.

1. Zamknij okienko **Dane wyjściowe** w Visual Studio.

   ![Zamknij okienko Dane wyjściowe w Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. W Visual Studio naciśnij **klawisze Ctrl** + **S,** aby zapisać aplikację.

1. Zamknij program Visual Studio.

## <a name="review-code-complete"></a>Przegląd: ukończony kod

W tym samouczku w aplikacji kalkulatora wdaliśmy się w wiele zmian. Aplikacja teraz wydajniej obsługuje zasoby obliczeniowe i obsługuje większość błędów wejściowych użytkownika.

Oto kompletny kod w jednym miejscu:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Następne kroki

:::moniker range="vs-2017"

Przejdź do kolejnych samouczków:

> [!div class="nextstepaction"]
> [Samouczki języka C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Przewodnik po środowisku IDE programu Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Przejdź do drugiej części tego samouczka:

> [!div class="nextstepaction"]
> [Samouczek, część 2: korzystanie z wielu projektów i pakietów innych firm](tutorial-console-part-2.md)
:::moniker-end

Ponadto warto:

- [Kontynuuj pracę z większej liczby samouczków języka C#](/dotnet/csharp/tutorials/)
- [Szybki start: tworzenie aplikacji ASP.NET Core internetowej](../../ide/quickstart-aspnet-core.md)
- [Dowiedz się, jak debugować kod C# w Visual Studio](tutorial-debugger.md)
- Wskazówki dotyczące tworzenia i uruchamiania [testów jednostkowych](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Uruchamianie programu w języku C#](run-program.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Kontynuuj pracę z Visual Studio IDE](/../visual-studio-ide.md)