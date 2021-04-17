---
title: 'Samouczek: rozszerzanie prostej aplikacji konsolowej C#'
description: Dowiedz się, jak tworzyć aplikację konsolową w języku C# Visual Studio, krok po kroku.
ms.custom: get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cce069b1c4acb1784388b7afb06e810dbe826d59
ms.sourcegitcommit: 54aac5044a9853a435577acc5a134cb254494ffb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2021
ms.locfileid: "107584130"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Samouczek: rozszerzanie prostej aplikacji konsolowej C#

Z tego samouczka dowiesz się, jak za pomocą Visual Studio rozszerzyć aplikację konsoli utworzoną w pierwszej części. Poznasz niektóre funkcje usługi Visual Studio, które będą potrzebne do codziennego tworzenia aplikacji, takie jak zarządzanie wieloma projektami i odwoływanie się do pakietów innych firm.

Jeśli pierwsza część tej serii została [ukończona,](tutorial-console.md) masz już aplikację konsolą Calculator.  Aby pominąć część 1, możesz rozpocząć od otwarcia projektu z repozytorium GitHub. Aplikacja Kalkulator języka C# znajduje się w repocie [vs-tutorial-samples,](https://github.com/MicrosoftDocs/vs-tutorial-samples)więc możesz po prostu wykonać kroki opisane w tece Samouczek: otwieranie projektu z [repo,](../tutorial-open-project-from-repo.md) aby rozpocząć pracę.

## <a name="add-a-new-project"></a>Dodawanie nowego projektu

Rzeczywisty kod obejmuje wiele projektów, które współpracują ze sobą w ramach rozwiązania. Teraz dodajmy kolejny projekt do aplikacji Calculator. Będzie to biblioteka klas, która udostępnia niektóre funkcje kalkulatora.

1. Na platformie Visual Studio można użyć polecenia menu najwyższego poziomu File Add New Project (Dodaj nowy projekt), aby dodać nowy projekt, ale możesz również kliknąć prawym przyciskiem myszy nazwę istniejącego projektu (nazywanego "węzłem projektu") i otworzyć menu skrótów projektu  >    >   (lub menu kontekstowe). To menu skrótów zawiera wiele sposobów dodawania funkcji do projektów. Dlatego kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań **,** a następnie wybierz **polecenie Dodaj**  >  **nowy projekt.**

1. Wybierz szablon projektu języka C# **Biblioteka klas (.NET Standard).**

   ![Zrzut ekranu przedstawiający wybór szablonu projektu biblioteki klas](media/vs-2019/calculator2-add-project-dark.png)

1. Wpisz nazwę projektu **CalculatorLibrary** i wybierz pozycję **Utwórz**. Ponownie wybierz pozycję .NET 3.1 po wybraniu monitu. Visual Studio tworzy nowy projekt i dodaje go do rozwiązania.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań dodanym projektem biblioteki klas CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Zamiast pliku *Class1.cs* zmień nazwę pliku **CalculatorLibrary.cs.** Możesz kliknąć nazwę w oknie **Eksplorator rozwiązań** zmienić jej nazwę lub kliknąć prawym przyciskiem myszy i wybrać polecenie Zmień nazwę **lub** nacisnąć klawisz **F2.**

   Może pojawić się pytanie, czy chcesz zmienić nazwę wszelkich odwołań `Class1` do w pliku. Nie ma znaczenia, jak udzielisz odpowiedzi, ponieważ zastąpisz kod w przyszłym kroku.

1. Teraz musimy dodać odwołanie do projektu, aby pierwszy projekt może używać interfejsów API ujawnionych przez nową bibliotekę klas.  Kliknij prawym przyciskiem myszy węzeł **Zależności w** pierwszym projekcie i wybierz polecenie Dodaj odwołanie **do projektu**.

   ![Zrzut ekranu przedstawiający element menu Dodaj odwołanie do projektu](media/vs-2019/calculator2-add-project-reference-dark.png)

   Zostanie **wyświetlone okno dialogowe Menedżer** odwoływać się. To okno dialogowe umożliwia dodawanie odwołań do innych projektów, a także zestawów i bibliotek DLL COM potrzebnych w projektach.

   ![Zrzut ekranu okna dialogowego Menedżer odwoływać](media/vs-2019/calculator2-ref-manager-dark.png)

1. W **oknie dialogowym Menedżer** odwoływać zaznacz pole wyboru projektu **CalculatorLibrary** i wybierz przycisk **OK.**  Odwołanie do projektu jest wyświetlane w **węźle Projekty** w **Eksplorator rozwiązań**.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z odwołaniem do projektu](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. W *program.cs* wybierz klasę i cały jej kod, a następnie `Calculator` naciśnij klawisze **CTRL+X,** aby wytnij ją z programu Program.cs. Następnie w **oknie CalculatorLibrary** w *oknie CalculatorLibrary.cs* wklej kod do przestrzeni `CalculatorLibrary` nazw . Następnie należy wprowadzić klasę Calculator, `public` aby uwidocznić ją poza biblioteką. Kod w *calculatorLibrary.cs* powinien teraz przypominać następujący kod:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. Pierwszy projekt zawiera odwołanie, ale zobaczysz błąd, który nie został rozwiązany przez wywołanie Calculator.DoOperation. Wynika to z tego, że calculatorLibrary znajduje się w innej przestrzeni nazw, więc dodaj `CalculatorLibrary` przestrzeń nazw dla w pełni kwalifikowanego odwołania.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Zamiast tego spróbuj dodać dyrektywę using na początku pliku:

   ```csharp
   using CalculatorLibrary;
   ```

   Ta zmiana powinna umożliwiać usunięcie przestrzeni nazw CalculatorLibrary z witryny wywołań, ale teraz istnieje niejednoznaczność. Czy `Calculator` klasa znajduje się w klasie CalculatorLibrary, czy też jest przestrzenią nazw Calculator?  Aby rozwiązać niejednoznaczność, zmień nazwę przestrzeni nazw `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Odwołania do bibliotek .NET: zapis w dzienniku

1. Załóżmy, że chcesz teraz dodać dziennik wszystkich operacji i zapisać go w pliku tekstowym. Klasa .NET `Trace` udostępnia tę funkcję. (Jest to również przydatne w przypadku podstawowych technik debugowania drukowania).  Klasa Trace znajduje się w klasie System.Diagnostics i będziemy potrzebować klas System.IO, takich jak , więc zacznij od dodania dyrektyw using w górnej części `StreamWriter` *plików CalculatorLibrary.cs:*

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Patrząc na sposób, w jaki jest używana klasa Trace, należy przytrzymać odwołanie do klasy , która jest skojarzona z plikiem nadrzędnym. Oznacza to, że kalkulator będzie działać lepiej jako obiekt, więc dodajmy konstruktor na początku klasy Calculator w *calculatorLibrary.cs.*

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Musimy zmienić metodę statyczną `DoOperation` na metodę członkowskią, więc usuń słowo `static` kluczowe .  Dodajmy również dane wyjściowe do każdego obliczenia dla dziennika, tak aby metoda DoOperation wyglądała jak następujący kod:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Teraz z powrotem w *programie Program.cs* wywołanie statyczne jest oflagowane z czerwoną chybieńą. Aby rozwiązać ten problem, `calculator` utwórz zmienną, dodając następujący wiersz tuż przed `while (!endApp)` pętlą:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Zmodyfikuj witrynę wywołań w następujący sposób, aby odwoływali się do obiektu o nazwie małymi literami, dzięki czemu będzie to wywołanie członka, a nie wywołanie metody `DoOperation` `calculator` statycznej:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Uruchom program ponownie, a po jego Eksplorator plików kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie Otwórz folder w **programie Eksplorator plików**, a następnie przejdź w dół w Eksplorator plików do folderu wyjściowego. Może to być *bin/Debug/netcoreapp3.1* i otwórz plik *calculator.log.*

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Na tym etapie *calculatorLibrary.cs* powinien wyglądać podobnie do tego:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

A *program.cs* powinien wyglądać następująco:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Dodawanie pakietu NuGet: zapis do pliku JSON

1. Teraz załóżmy, że chcemy wyprowadzić operacje w formacie JSON, popularnym i przenośnym formacie do przechowywania danych obiektów. Aby zaimplementować tę funkcję, musimy odwoływać się do pakietu NuGet, Newtonsoft.Jsna. Pakiety NuGet są podstawowym celem dystrybucji bibliotek klas .NET. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy  węzeł Zależności dla projektu CalculatorLibrary, a następnie wybierz pozycję Zarządzaj **pakietami NuGet.**

   ![Zrzut ekranu przedstawiający zarządzanie pakietami NuGet w menu skrótów](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Zostanie otwarty Menedżer pakietów NuGet.

   ![Zrzut ekranu przedstawiający Menedżer pakietów NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Wyszukaj pozycję Newtonsoft.Jsw pakiecie, a następnie wybierz pozycję **Zainstaluj**.

   ![Zrzut ekranu przedstawiający informacje o pakiecie Newtonsoft NuGet](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Pakiet zostanie pobrany i dodany do projektu, a nowy wpis pojawi się w węźle Odwołania w **Eksplorator rozwiązań**.

1. Dodaj dyrektywę using dla System.IO i Newtonsoft.Jsna pakiecie na początku *calculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Teraz zastąp konstruktor kalkulatora następującym kodem i utwórz obiekt członkowski JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. `DoOperation`Zmodyfikuj metodę , aby dodać kod zapisujący JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Musisz dodać metodę , aby zakończyć składnię JSON, gdy użytkownik zakończy wprowadzanie danych operacji.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. A w *programie Program.cs* dodaj wywołanie finish na końcu.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Skompilowanie i uruchomienie aplikacji. Po wprowadzeniu kilku operacji zamknij aplikację prawidłowo przy użyciu polecenia "n".  Teraz otwórz plik calculatorlog.jspowinien zostać wyświetlony ekran podobny do następującego:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Debugowanie: ustawianie i trafianie punktu przerwania

Debuger Visual Studio to zaawansowane narzędzie, które umożliwia uruchamianie kodu krok po kroku w celu znalezienia dokładnego punktu, w którym popełniliśmy błąd programistyki. Następnie zrozumiesz, jakie poprawki należy wprowadzić w kodzie. Visual Studio można wprowadzać tymczasowe zmiany, aby można było kontynuować uruchamianie programu.

1. W *pliku Program.cs* kliknij margines z lewej strony następującego kodu (lub otwórz menu skrótów i wybierz pozycję **Wstaw** punkt przerwania punktu przerwania lub naciśnij  >  klawisz **F9):**

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Czerwony okrąg, który zostanie wyświetlony, wskazuje punkt przerwania. Możesz użyć punktów przerwania, aby wstrzymać aplikację i sprawdzić kod. Punkt przerwania można ustawić w dowolnym wierszu kodu wykonywalnego.

   ![Zrzut ekranu przedstawiający ustawianie punktu przerwania](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Skompiluj i uruchom aplikację.

1. W uruchomionej aplikacji wpisz niektóre wartości dla obliczenia:

   - Jako pierwszą liczbę wpisz **8** i wprowadź ją.
   - Jako drugą liczbę wpisz **0** i wprowadź ją.
   - Dla operatora bawmy się trochę. wpisz **d** i wprowadź go.

   Aplikacja wstrzymuje miejsce utworzenia punktu przerwania, co jest wskazywane przez żółty wskaźnik po lewej stronie i wyróżniony kod. Wyróżniony kod nie został jeszcze wykonany.

   ![Zrzut ekranu przedstawiający trafienie punktu przerwania](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Teraz po wstrzymaniu aplikacji możesz sprawdzić stan aplikacji.

## <a name="debug-view-variables"></a>Debugowanie: wyświetlanie zmiennych

1. W wyróżniony kod zatrzymaj wskaźnik myszy na zmiennych, takich jak `cleanNum1` i `op` . Zostaną wyświetlone bieżące wartości tych zmiennych ( `8` i `d` , odpowiednio), które są wyświetlane w etykietkach danych.

   ![Zrzut ekranu przedstawiający wyświetlanie etykietki danych](media/vs-2019/calculator-2-debug-view-datatip.png)

   Podczas debugowania sprawdzanie, czy zmienne są w stanie przechowywać wartości, których oczekujesz, często ma kluczowe znaczenie dla rozwiązywania problemów.

2. W dolnym okienku przyjrzyj się **oknie Ustawienia** lokalne. (Jeśli jest zamknięty, wybierz pozycję **Debuguj**  >  **Windows**  >  **Locals** to open it.)

   W oknie Zmienne lokalne zobaczysz każdą zmienną, która znajduje się obecnie w zakresie, wraz z jej wartością i typem.

   ![Zrzut ekranu przedstawiający okno Locals (Lokalne)](media/vs-2019/calculator-2-debug-locals-window.png)

3. Spójrz na **okno Automatyczne.**

   Okno Autos (Automatyczne)  jest podobne do okna Zmiennych lokalnych, ale zawiera zmienne bezpośrednio poprzedzające bieżący wiersz kodu, w którym aplikacja jest wstrzymana, i następujące po nim.

   Następnie wykonasz kod w debugerze po jednej instrukcji na raz, która jest nazywana wykonywaniem *krokowym*.

## <a name="debug-step-through-code"></a>Debugowanie: krok po kroku w kodzie

1. Naciśnij **klawisz F11** (lub **Debuguj**  >  **krok do**).

   Za pomocą polecenia Step Into aplikacja wykonuje bieżącą instrukcje i przejść do następnej instrukcji wykonywalnego (zazwyczaj następnego wiersza kodu). Żółty wskaźnik po lewej stronie zawsze wskazuje bieżącą instrukcje.

   ![Zrzut ekranu przedstawiający polecenie krok do kroku](media/vs-2019/calculator-2-debug-step-into.png)

   Właśnie doszliśmy do metody `DoOperation` w `Calculator` klasie .

1. Aby uzyskać hierarchiczny podgląd przepływu programu, spójrz na okno **Stos** wywołań. (Jeśli jest zamknięty, wybierz pozycję **Debuguj**  >  **Windows**  >  **Stos wywołań).**

   ![Zrzut ekranu przedstawiający stos wywołań](media/vs-2019/calculator-2-debug-call-stack.png)

   Ten widok przedstawia bieżącą metodę wskazywaną przez żółty wskaźnik, a drugi wiersz przedstawia funkcję, która ją nazwała, z metody w `Calculator.DoOperation` `Main` *programie Program.cs*. Okno **Stos wywołań** pokazuje kolejność wywoływania metod i funkcji. Ponadto zapewnia dostęp do wielu funkcji debugera, takich jak **przejdź** do kodu źródłowego , z menu skrótów.

1. Naciśnij **kilka razy klawisz F10** (lub **Debuguj** krok  >  **powyżej),** aż aplikacja wstrzyma się na instrukcji `switch` .

   ```csharp
   switch (op)
   {
   ```

   Polecenie Step Over jest podobne do polecenia Step Into, z tą różnicą, że jeśli bieżąca instrukcja wywołuje funkcję, debuger uruchamia kod w wywołanej funkcji i nie wstrzymuje wykonywania do momentu powrotu funkcji. Funkcja Step Over to szybszy sposób nawigowania po kodzie, jeśli nie interesuje Cię określonej funkcji.

1. Naciśnij jeszcze raz klawisz **F10,** aby aplikacja wstrzymała się w następującym wierszu kodu.

   ```csharp
   if (num2 != 0)
   {
   ```

   Ten kod sprawdza, czy nie ma przypadku dzielenia przez zero. Jeśli aplikacja będzie kontynuować, zrzuci wyjątek ogólny (błąd), ale załóżmy, że rozważysz tę usterkę i chcesz zrobić coś innego, na przykład wyświetlić rzeczywistą zwróconą wartość w konsoli. Jedną z opcji jest użycie funkcji debugera o nazwie Edytuj i kontynuuj, aby wprowadzać zmiany w kodzie, a następnie kontynuować debugowanie. Jednak pokażemy Ci inny sposób na tymczasowe zmodyfikowanie przepływu wykonywania.

## <a name="debug-test-a-temporary-change"></a>Debugowanie: testowanie tymczasowej zmiany

1. Wybierz żółty wskaźnik, obecnie wstrzymany na instrukcji , i `if (num2 != 0)` przeciągnij go do następującej instrukcji.

   ```csharp
   result = num1 / num2;
   ```

   W ten sposób aplikacja całkowicie pomija instrukcje , aby zobaczyć, co się stanie, gdy `if` podzielisz przez zero.

1. Naciśnij **klawisz F10,** aby wykonać wiersz kodu.

1. Zatrzymaj wskaźnik myszy na zmiennej `result` i zobaczysz, że przechowuje ona wartość `Infinity` .

   W języku C# `Infinity` wynik jest wynikiem dzielenia przez zero.

1. Naciśnij **klawisz F5** (lub **debuguj**  >  **kontynuuj debugowanie).**

   Symbol nieskończoności pojawia się w konsoli w wyniku operacji matematycznych.

1. Zamknij aplikację prawidłowo przy użyciu polecenia "n".

## <a name="code-complete"></a>Ukończony kod

Oto kompletny kod pliku *CalculatorLibrary.cs* po ukończeniu wszystkich kroków:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

A oto kod dla programu *Program.cs:* 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Aby dowiedzieć się więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj pracę z większej liczby samouczków języka C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Kontynuuj pracę z omówieniem Visual Studio IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Zobacz też

- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Dowiedz się, jak debugować kod C# w Visual Studio](tutorial-debugger.md)
