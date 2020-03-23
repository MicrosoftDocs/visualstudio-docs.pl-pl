---
title: 'Samouczek: Tworzenie prostej aplikacji konsoli języka C#'
description: Dowiedz się, jak utworzyć aplikację konsoli języka C# w programie Visual Studio, krok po kroku.
ms.custom: seodec18, get-started
ms.date: 02/18/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 528887c477814b7011cf941a9198f83701beee54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "78215435"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Samouczek: Tworzenie prostej aplikacji konsoli języka C# w programie Visual Studio

W tym samouczku dla języka C#, użyjesz programu Visual Studio do tworzenia i uruchamiania aplikacji konsoli i eksplorować niektóre funkcje zintegrowanego środowiska programistycznego programu Visual Studio (IDE) podczas wykonywania tej operacji.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzymy projekt aplikacji języka C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.
   (Alternatywnie, naciśnij **klawisze Ctrl**+**Shift**+**N**).

3. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **C#,** a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij plik ***Kalkulator***.

   ![Szablon projektu aplikacji konsoli (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu **aplikacji konsoli (.NET Core),** możesz go uzyskać, dodając obciążenie **programistyczne .NET Core dla różnych platform.** Oto jak to zrobić.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Korzystanie z okna dialogowego Nowy projekt

1. Wybierz łącze **Otwórz Instalatora programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**

   ![Wybieranie łącza Instalator programu Visual Studio w oknie dialogowym Nowy projekt](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

   ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anulowanie z okna dialogowego **Nowy projekt** i na górnym pasku menu wybierz pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# dla aplikacji konsoli (.NET Framework)](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji konsoli (.NET Core),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio wybierz obciążenie **programistyczne .NET Core na różnych platformach.**
   >
   > ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *kalkulator* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "Kalkulator"](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio otwiera nowy projekt, który zawiera domyślny kod "Hello World".
   
::: moniker-end

## <a name="create-the-app"></a>Tworzymy aplikację.

Najpierw zbadamy niektóre podstawowe obliczenia liczby całkowitej w języku C#. Następnie dodamy kod, aby utworzyć podstawowy kalkulator. Następnie debugujemy aplikację, aby znaleźć i naprawić błędy. Na koniec udoskonalimy kod, aby był bardziej wydajny.

### <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Zacznijmy od podstawowej matematyki całkowitej w języku C#.

1. W edytorze kodu usuń domyślny kod "Hello World".

    ![Usuń domyślny kod Hello World z nowej aplikacji kalkulatora](./media/csharp-console-calculator-deletehelloworld.png)

   W szczególności usuń wiersz, `Console.WriteLine("Hello World!");`który mówi, .

1. W jego miejsce wpisz następujący kod:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Należy zauważyć, że po wykonaniu tej funkcji IntelliSense w programie Visual Studio oferuje możliwość autouzupełnienia wpisu.

    > [!NOTE]
    > Poniższa animacja nie jest przeznaczona do duplikowania poprzedniego kodu. Jest przeznaczony tylko do pokazania, jak działa funkcja autouzupełniania.

    ![Animacja kodu matematycznego liczby całkowitej, która pokazuje funkcję autouzupełnienia intellisense w programie Visual Studio IDE](./media/integer-math-intellisense.gif)

1. Wybierz zielony przycisk **Start** obok **pozycji Kalkulator,** aby zbudować i uruchomić program, lub naciśnij klawisz **F5**.

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację z paska narzędzi](./media/csharp-console-calculator-button.png)

   Otwiera się okno konsoli, które ujawnia sumę 42 + 119, która wynosi **161**.

    ![Okno konsoli z wynikami lekcji matematyki liczby całkowitej](./media/csharp-console-integer-math.png)

1. **(Opcjonalnie)** Można zmienić operatora, aby zmienić wynik. Na przykład można zmienić `+` operatora `int c = a + b;` w wierszu kodu `-` do `*` odejmowania, `/` mnożenia lub podziału. Następnie po uruchomieniu programu wynik również się zmienia.

1. Zamknij okno konsoli.

### <a name="add-code-to-create-a-calculator"></a>Dodawanie kodu w celu utworzenia kalkulatora

Kontynuujmy, dodając bardziej złożony zestaw kodu kalkulatora do projektu.

1. Usuń cały kod widoczny w edytorze kodu.

1. Wprowadź lub wklej następujący nowy kod do edytora kodu:

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

1. Wybierz **opcję Kalkulator,** aby uruchomić program, lub naciśnij klawisz **F5**.

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację z paska narzędzi](./media/csharp-console-calculator-button.png)

   Zostanie otwarte okno konsoli.

1. Wyświetl aplikację w oknie konsoli, a następnie postępuj zgodnie z instrukcjami, aby dodać numery **42** i **119**.

   Aplikacja powinna wyglądać podobnie do następującego zrzutu ekranu:

    ![Okno konsoli z aplikacją Kalkulator i zawiera monity o podjęcie czynności](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Dodawanie funkcji do kalkulatora

Dostosujmy kod, aby dodać dodatkowe funkcje.

### <a name="add-decimals"></a>Dodawanie miejsc dziesiętnych

Aplikacja kalkulatora aktualnie akceptuje i zwraca liczby pełne. Ale będzie bardziej precyzyjne, jeśli dodamy kod, który pozwala na miejsca dziesiętne.

Podobnie jak na poniższym zrzucie ekranu, jeśli uruchomisz aplikację i podzielisz liczbę 42 przez liczbę 119, wynik wynosi 0 (zero), co nie jest dokładne.

![Okno konsoli z aplikacją Kalkulator, która nie zwraca liczby dziesiętnej w wyniku](./media/csharp-console-calculator-nodecimal.png)

Naprawmy kod tak, aby obsługiwał miejsca dziesiętne.

1. Naciśnij **klawisz Ctrl** + **F,** aby otworzyć kontrolę **Znajdź i zamień.**

1. Zmień każde wystąpienie zmiennej na `int` `float`.

   Upewnij się, że w formancie **Znajdź i Zamień** przełączyć dopasowanie **sprawy** (**Alt**+**C**) i **Dopasuj całe słowo** (**Alt**+**W).**

    ![Animacja formantu Znajdź i zamień pokazująca, jak zmienić zmienną int na float](./media/find-replace-control-animation.gif)

1. Uruchom ponownie aplikację kalkulatora i podziel liczbę **42** przez liczbę **119**.

   Należy zauważyć, że aplikacja zwraca teraz cyfrę dziesiętną zamiast zera.

    ![Okno konsoli z aplikacją Kalkulator, która zwraca teraz cyfrę dziesiętną](./media/csharp-console-calculator-decimal.png)

Jednak aplikacja tworzy tylko wynik dziesiętny. Zróbmy kilka poprawek do kodu, aby aplikacja mogła obliczyć również miejsca dziesiętne.

1. Użyj kontrolki **Znajdź i zamień** (**Ctrl** +  `double`**F**), aby zmienić każde wystąpienie zmiennej na `float` , i zmienić każde wystąpienie metody na `Convert.ToInt32` `Convert.ToDouble`.

1. Uruchom aplikację kalkulatora i podzielić liczbę **42.5** przez numer **119.75**.

   Należy zauważyć, że aplikacja akceptuje teraz wartości dziesiętne i zwraca dłuższy numer dziesiętny jako jego wynik.

    ![Okno konsoli z aplikacją Kalkulator, która teraz akceptuje liczby dziesiętne i zwraca dłuższą cyfrę dziesiętną w wyniku](./media/csharp-console-calculator-usedecimals.png)

    (Naprawimy liczbę miejsc dziesiętnych w sekcji [Poprawianie kodu).](#revise-the-code)

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ulepszyliśmy naszą podstawową aplikację kalkulatora, ale nie ma jeszcze sejfów, które obsługują wyjątki, takie jak błędy wprowadzania danych przez użytkownika.

Na przykład jeśli spróbujesz podzielić liczbę przez zero lub wprowadzić znak alfa, gdy aplikacja oczekuje znaku numerycznego (lub odwrotnie), aplikacja może przestać działać, zwrócić błąd lub zwrócić nieoczekiwany wynik nienumeryczny.

Przejdźmy przez kilka typowych błędów wprowadzania danych użytkownika, zlokalizujmy je w debugerze, jeśli się tam pojawią, i napraw je w kodzie.

> [!TIP]
> Aby uzyskać więcej informacji na temat debugera i jak to działa, zobacz Pierwsze spojrzenie na stronie [debugera programu Visual Studio.](../../debugger/debugger-feature-tour.md)

### <a name="fix-the-divide-by-zero-error"></a>Napraw błąd "podziel przez zero"

Podczas próby podzielenia liczby przez zero aplikacja konsoli może zostać zamarzona, a następnie pokazać, co jest nie tak w edytorze kodu.

   ![Edytor kodu programu Visual Studio pokazuje błąd dzielenia przez zero](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Czasami aplikacja nie zawiesza się, a debuger nie będzie wyświetlał błędu dzielenia przez zero. Zamiast tego aplikacja może zwrócić nieoczekiwany wynik nieliczeryczny, taki jak symbol nieskończoności. Następująca poprawka kodu nadal ma zastosowanie.

Zmieńmy kod, aby obsłużyć ten błąd.

1. Usuń kod, który pojawia `case "d":` się bezpośrednio `// Wait for the user to respond before closing`między i komentarz, który mówi .

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

   Po dodaniu kodu sekcja z `switch` instrukcją powinna wyglądać podobnie do następującego zrzutu ekranu:

   ![Poprawiona sekcja "przełącz" w edytorze kodu programu Visual Studio](./media/csharp-console-calculator-switch-code.png)

Teraz, gdy podzielisz dowolną liczbę przez zero, aplikacja poprosi o inny numer. Jeszcze lepiej: nie przestanie pytać, dopóki nie podasz numeru innego niż zero.

   ![Edytor kodu programu Visual Studio pokazuje błąd dzielenia przez zero](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Naprawianie błędu "formatu"

Jeśli wprowadzisz znak alfa, gdy aplikacja oczekuje znaku numerycznego (lub odwrotnie), aplikacja konsoli zawiesza się. Visual Studio następnie pokazuje, co jest nie tak w edytorze kodu.

   ![Edytor kodu programu Visual Studio wyświetla błąd formatu](./media/csharp-console-calculator-format-error.png)

Aby naprawić ten błąd, musimy refaktoryzować kod, który wcześniej wprowadziliśmy.

#### <a name="revise-the-code"></a>Zmiana kodu

Zamiast polegać `program` na klasie do obsługi całego kodu, podzielimy `Calculator` naszą `Program`aplikację na dwie klasy: i .

Klasa `Calculator` będzie obsługiwać większość pracy obliczeń, a `Program` klasa będzie obsługiwać interfejs użytkownika i pracy przechwytywania błędów.

Zacznijmy.

1. Usuń wszystko `Calculator` w obszarze nazw między jego otwieraniem i zamykaniem nawiasów klamrowych:

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

1. Następnie dodaj nową `Program` klasę w następujący sposób:

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

1. Wybierz **opcję Kalkulator,** aby uruchomić program, lub naciśnij klawisz **F5**.

1. Postępuj zgodnie z instrukcjami i podziel liczbę **42** przez liczbę **119**. Aplikacja powinna wyglądać podobnie do następującego zrzutu ekranu:

    ![Okno konsoli z refaktoryzowanym kalkulatorem zawiera monity o podjęcie działań i obsługę błędów w przypadku nieprawidłowych danych wejściowych](./media/csharp-console-calculator-refactored.png)

    Należy zauważyć, że masz możliwość wprowadzania większej liczby równań, dopóki nie zdecydujesz się zamknąć aplikacji konsoli. Zmniejszyliśmy również liczbę miejsc dziesiętnych w wyniku.

## <a name="close-the-app"></a>Zamykanie aplikacji

1. Jeśli jeszcze tego nie zrobiłeś, zamknij aplikację kalkulatora.

1. Zamknij okienko **dane wyjściowe** w programie Visual Studio.

   ![Zamykanie okienka dane wyjściowe w programie Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. W programie Visual Studio naciśnij klawisz **Ctrl**+**S,** aby zapisać aplikację.

1. Zamknij program Visual Studio.

## <a name="code-complete"></a>Kod kompletny

W tym samouczku wyemiorowaliśmy wiele zmian w aplikacji kalkulatora. Aplikacja obsługuje teraz zasoby obliczeniowe bardziej efektywnie i obsługuje większość błędów wejściowych użytkownika.

Oto pełny kod, wszystko w jednym miejscu:

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

Gratulujemy ukończenia tego samouczka! Aby dowiedzieć się jeszcze więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj więcej samouczków języka C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Zobacz też

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Dowiedz się, jak debugować kod C# w programie Visual Studio](tutorial-debugger.md)
