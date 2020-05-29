---
title: 'Samouczek: tworzenie prostej aplikacji konsolowej w języku C#'
description: Dowiedz się, jak utworzyć aplikację konsolową w języku C# w programie Visual Studio, krok po kroku.
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
ms.openlocfilehash: 00798f5eb7261df0a039c82566018cbb0efe710a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183291"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Samouczek: tworzenie prostej aplikacji konsolowej w języku C# w programie Visual Studio

W tym samouczku dla języka C# będziesz używać programu Visual Studio do tworzenia i uruchamiania aplikacji konsolowej oraz eksplorowania niektórych funkcji zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzymy projekt aplikacji w języku C#. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.
   (Alternatywnie naciśnij klawisz **Ctrl** + **SHIFT** + **N**).

3. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nazwij ***Kalkulator***plików.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli szablon projektu **Aplikacja konsolowa (.NET Core)** nie jest widoczny, można go uzyskać, dodając obciążenie **Międzyplatformowe platformy .NET Core** . Oto jak to zrobić.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: korzystanie z okna dialogowego Nowy projekt

1. Wybierz łącze **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

   ![Wybierz łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

   ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu narzędzi

1. Anuluj okno dialogowe **Nowy projekt** , a następnie z górnego paska menu wybierz kolejno opcje **Narzędzia** > **Pobierz narzędzia i funkcje**.

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie szablonu C# dla aplikacji konsolowej (.NET Framework)](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *Kalkulator* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" Nadaj nazwę projektowi "Kalkulator"](./media/vs-2019/csharp-name-your-calculator-project.png)

   Program Visual Studio otwiera nowy projekt, który zawiera domyślny kod "Hello world".
   
::: moniker-end

## <a name="create-the-app"></a>Tworzymy aplikację.

Najpierw będziemy poznać niektóre podstawowe wartości matematyczne w języku C#. Następnie dodamy kod, aby utworzyć podstawowy Kalkulator. Następnie debugujemy aplikację w celu znalezienia i naprawienia błędów. A wreszcie będziemy udoskonalić kod w celu zwiększenia wydajności.

### <a name="explore-integer-math"></a>Poznawanie matematyki całkowitoliczbowej

Zacznijmy od niektórych podstawowych obliczeń matematycznych w języku C#.

1. W edytorze kodu, Usuń domyślny kod "Hello world".

    ![Usuń domyślny kod Hello world z nowej aplikacji kalkulatora](./media/csharp-console-calculator-deletehelloworld.png)

   W celu usunięcia wiersza, który mówi, `Console.WriteLine("Hello World!");` .

1. W tym miejscu wpisz następujący kod:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Należy zauważyć, że po wykonaniu tej czynności funkcja IntelliSense w programie Visual Studio oferuje opcję Autouzupełnianie wpisu.

    > [!NOTE]
    > Poniższa animacja nie jest przeznaczona do duplikowania poprzedniego kodu. Tylko pokazuje, jak działa funkcja autouzupełniania.

    ![Animacja kodu matematycznego w postaci liczby całkowitej, który pokazuje funkcję Autouzupełnianie funkcji IntelliSense w środowisku IDE programu Visual Studio](./media/integer-math-intellisense.gif)

1. Wybierz zielony przycisk **Start** obok pozycji **Kalkulator** , aby skompilować i uruchomić program, lub naciśnij klawisz **F5**.

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację z paska narzędzi](./media/csharp-console-calculator-button.png)

   Zostanie otwarte okno konsoli, które pokazuje sumę 42 + 119, która jest **161**.

    ![Okno konsoli przedstawiające wyniki obliczeń liczb całkowitych](./media/csharp-console-integer-math.png)

1. **(Opcjonalnie)** Można zmienić operatora, aby zmienić wynik. Na przykład, można zmienić `+` operator w `int c = a + b;` wierszu kodu na `-` odejmowanie, `*` dla mnożenia lub `/` dzielenia. Następnie, gdy uruchomisz program, wynik zostanie również zmieniony.

1. Zamknij okno konsoli.

### <a name="add-code-to-create-a-calculator"></a>Dodawanie kodu w celu utworzenia kalkulatora

Kontynuujmy Dodawanie bardziej złożonego zestawu kodu kalkulatora do projektu.

1. Usuń cały kod widoczny w edytorze kodu.

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

1. Wybierz **Kalkulator** , aby uruchomić program, lub naciśnij klawisz **F5**.

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację z paska narzędzi](./media/csharp-console-calculator-button.png)

   Zostanie otwarte okno konsoli.

1. Wyświetl aplikację w oknie konsoli, a następnie postępuj zgodnie z monitami, aby dodać numery **42** i **119**.

   Aplikacja powinna wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z aplikacją kalkulatora i zawiera monity o akcje do wykonania](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Dodawanie funkcji do kalkulatora

Dostosujmy kod, aby dodać więcej funkcji.

### <a name="add-decimals"></a>Dodaj miejsca dziesiętne

Aplikacja kalkulatora aktualnie akceptuje i zwraca liczby całkowite. Jednak będzie bardziej precyzyjna, Jeśli dodamy kod, który umożliwia używanie wartości dziesiętnych.

Tak jak na poniższym zrzucie ekranu, jeśli uruchomisz aplikację i podzielę liczbę 42 przez liczbę 119, wynik ma wartość 0 (zero), co nie jest dokładne.

![Okno konsoli z aplikacją kalkulatora, która nie zwraca cyfry dziesiętnej w wyniku](./media/csharp-console-calculator-nodecimal.png)

Naprawianie kodu, aby obsługiwały miejsca dziesiętne.

1. Naciśnij klawisz **Ctrl**  +  **H** , aby otworzyć formant **Znajdowanie i zamienianie** .

1. Zmień każde wystąpienie `int` zmiennej na `float` .

   Upewnij się, że w kontrolce Znajdź i Zamień zostanie przełączona wartość **Uwzględnij wielkość liter** (**Alt** + **C**) i **dopasowanie do całego wyrazu** (**Alt** + **W**). **Find and Replace**

    ![Animacja kontrolki Znajdź i Zamień pokazująca, jak zmienić zmienną int na wartość zmiennoprzecinkową](./media/find-replace-control-animation.gif)

1. Ponownie uruchom aplikację Kalkulator i Podziel liczbę **42** przez liczbę **119**.

   Zauważ, że aplikacja zwraca teraz cyfrę dziesiętną zamiast wartości zero.

    ![Okno konsoli z aplikacją kalkulatora, która teraz zwraca cyfrę dziesiętną w wyniku](./media/csharp-console-calculator-decimal.png)

Jednak aplikacja generuje tylko wynik dziesiętny. Przyjrzyjmy się do kodu, aby aplikacja mogła również obliczyć liczbę miejsc dziesiętnych.

1. Użyj kontrolki **Znajdź i Zamień** (**Ctrl**  +  **H**), aby zmienić każde wystąpienie `float` zmiennej na `double` , i zmienić każde wystąpienie `Convert.ToInt32` metody na `Convert.ToDouble` .

1. Uruchom aplikację Kalkulator i Podziel liczbę **42,5** przez liczbę **119,75**.

   Zauważ, że aplikacja akceptuje wartości dziesiętne i zwraca dłuższą cyfrę dziesiętną jako wynik.

    ![Okno konsoli z aplikacją kalkulatora, która akceptuje liczby dziesiętne i zwraca dłuższą cyfrę dziesiętną w wyniku](./media/csharp-console-calculator-usedecimals.png)

    (Poprawimy liczbę miejsc dziesiętnych w sekcji [Popraw kod](#revise-the-code) ).

## <a name="debug-the-app"></a>Debugowanie aplikacji

Ulepszono nasze podstawowe aplikacje kalkulatora, ale nie ma jeszcze bezpieczeństwa w miejscu, w którym można obsługiwać wyjątki, takie jak błędy danych wejściowych użytkownika.

Na przykład jeśli spróbujesz podzielić liczbę przez zero lub wprowadzić znak alfanumeryczny, gdy aplikacja oczekuje znaku numerycznego (lub odwrotnie), aplikacja może przestać działać, zwracać błąd lub zwracać nieoczekiwany wynik nienumeryczny.

Zapoznaj się z kilkoma typowymi błędami danych wejściowych użytkownika, Znajdź je w debugerze, jeśli się tam znajdują, i napraw je w kodzie.

> [!TIP]
> Aby uzyskać więcej informacji o debugerze i sposobie jego działania, zobacz [pierwsze spojrzenie na stronę debugera programu Visual Studio](../../debugger/debugger-feature-tour.md) .

### <a name="fix-the-divide-by-zero-error"></a>Popraw błąd "dzielenie przez zero"

Przy próbie podzielenia liczby przez zero Aplikacja konsolowa może zostać zamrożona, a następnie pokazać, co jest niewłaściwe w edytorze kodu.

   ![Edytor kodu programu Visual Studio pokazuje błąd dzielenia przez zero](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Czasami aplikacja nie zawiesza się, a debuger nie pokazuje błędu dzielenia przez zero. Zamiast tego aplikacja może zwrócić nieoczekiwany wynik nienumeryczny, taki jak symbol nieskończoności. Następująca poprawka kodu nadal ma zastosowanie.

Zmieńmy kod, aby obsłużyć ten błąd.

1. Usuń kod, który pojawia się bezpośrednio między `case "d":` i komentarzem `// Wait for the user to respond before closing` .

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

   Po dodaniu kodu sekcja z `switch` instrukcją powinna wyglądać podobnie do poniższego zrzutu ekranu:

   ![Poprawiona sekcja "switch" w edytorze kodu programu Visual Studio](./media/csharp-console-calculator-switch-code.png)

Teraz, gdy podzielę dowolną liczbę przez zero, aplikacja będzie pytać o inną liczbę. Jeszcze lepsze: nie będzie ono zatrzymywać, dopóki nie zostanie wprowadzona liczba różna od zera.

   ![Edytor kodu programu Visual Studio pokazuje błąd dzielenia przez zero](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Popraw błąd "format"

Jeśli wprowadzisz znak alfanumeryczny, gdy aplikacja oczekuje znaku numerycznego (lub odwrotnie), aplikacja konsoli zostanie zamrożona. Program Visual Studio wyświetli następnie informacje o błędach w edytorze kodu.

   ![Edytor kodu programu Visual Studio pokazuje błąd formatu](./media/csharp-console-calculator-format-error.png)

Aby naprawić ten błąd, należy wcześniej wprowadzić kod.

#### <a name="revise-the-code"></a>Popraw kod

Zamiast polegać na `program` klasie, aby obsłużyć cały kod, Podziel aplikację na dwie klasy: `Calculator` i `Program` .

`Calculator`Klasa będzie obsługiwać zbiorcze zadania obliczeniowe, a `Program` Klasa będzie obsługiwać interfejs użytkownika i przechwytywanie błędów.

Zacznijmy.

1. Usuń wszystkie elementy w `Calculator` przestrzeni nazw między otwierającym i zamykającym nawiasem klamrowym:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Następnie Dodaj nową `Calculator` klasę w następujący sposób:

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

1. Następnie Dodaj nową `Program` klasę w następujący sposób:

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

1. Wybierz **Kalkulator** , aby uruchomić program, lub naciśnij klawisz **F5**.

1. Postępuj zgodnie z monitami i Podziel liczbę **42** przez liczbę **119**. Aplikacja powinna wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z zapytaniem do aplikacji kalkulatora refaktoryzacji, która zawiera monity o podejmowanych działaniach i obsłudze błędów dla nieprawidłowych danych wejściowych](./media/csharp-console-calculator-refactored.png)

    Zwróć uwagę, że możesz wprowadzić więcej równań, dopóki nie zostanie wybrana opcja zamknięcia aplikacji konsolowej. Ponadto zmniejszamy liczbę miejsc dziesiętnych w wyniku.

## <a name="close-the-app"></a>Zamknij aplikację

1. Jeśli jeszcze tego nie zrobiono, zamknij aplikację Kalkulator.

1. Zamknij okienko **danych wyjściowych** w programie Visual Studio.

   ![Zamknij okienko danych wyjściowych w programie Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. W programie Visual Studio naciśnij **kombinację klawiszy CTRL** + **S** , aby zapisać aplikację.

1. Zamknij program Visual Studio.

## <a name="code-complete"></a>Kod ukończony

W ramach tego samouczka wprowadziliśmy wiele zmian w aplikacji Kalkulator. Aplikacja teraz obsługuje zasoby obliczeniowe i obsługuje większość błędów danych wejściowych użytkownika.

Oto kompletny kod, wszystko w jednym miejscu:

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

Gratulujemy ukończenia tego samouczka. Aby dowiedzieć się jeszcze więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj pracę z więcej samouczkami w języku C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Zobacz także

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Informacje o debugowaniu kodu w języku C# w programie Visual Studio](tutorial-debugger.md)
