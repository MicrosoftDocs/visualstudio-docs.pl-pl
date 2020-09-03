---
title: 'Samouczek: zwiększanie prostej aplikacji konsolowej w języku C#'
description: Dowiedz się, jak utworzyć aplikację konsolową w języku C# w programie Visual Studio, krok po kroku.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 981f18857beb83ef2a4902f50985ca8e9f7ed901
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88507959"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Samouczek: zwiększanie prostej aplikacji konsolowej w języku C#

W tym samouczku dowiesz się, jak za pomocą programu Visual Studio zwiększyć aplikację konsolową utworzoną w pierwszej części. Poznasz niektóre funkcje programu Visual Studio, które będą potrzebne do codziennego opracowywania, na przykład zarządzanie wieloma projektami i odwoływanie się do pakietów innych firm.

Po ukończeniu [pierwszej części](tutorial-console.md) tej serii masz już aplikację konsolową Kalkulator.  Aby pominąć część 1, możesz zacząć od otwarcia projektu z repozytorium GitHub. Aplikacja kalkulatora języka C# znajduje się w [repozytorium vs-samouczek-przykłady](https://github.com/MicrosoftDocs/vs-tutorial-samples), więc możesz wykonać kroki opisane w [samouczku: Otwórz projekt z repozytorium](../tutorial-open-project-from-repo.md) , aby rozpocząć pracę.

## <a name="add-a-new-project"></a>Dodaj nowy projekt

Kod w języku rzeczywistym obejmuje wiele projektów współpracujących w rozwiązaniu. Teraz Dodajmy kolejny projekt do aplikacji Kalkulator. Będzie to Biblioteka klas, która udostępnia niektóre funkcje kalkulatora.

1. W programie Visual Studio można użyć pliku polecenia menu najwyższego poziomu **File**  >  **Dodaj**  >  **Nowy projekt** , aby dodać nowy projekt, ale można również kliknąć prawym przyciskiem myszy istniejącą nazwę projektu (nazywaną "węzłem projektu") i otworzyć menu skrótów projektu (lub menu kontekstowe). To menu skrótów zawiera wiele sposobów dodawania funkcjonalności do projektów. W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

1. Wybierz bibliotekę klas szablonu projektu C# **(.NET standard)**.

   ![Zrzut ekranu przedstawiający wybór szablonu projektu biblioteki klas](media/vs-2019/calculator2-add-project-dark.png)

1. Wpisz nazwę projektu **CalculatorLibrary**, a następnie wybierz pozycję **Utwórz**. Program Visual Studio tworzy nowy projekt i dodaje go do rozwiązania.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dodanym projektem biblioteki klas CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Zamiast *Class1.cs*należy zmienić nazwę pliku **CalculatorLibrary.cs**. Możesz kliknąć nazwę w **Eksplorator rozwiązań** , aby zmienić jej nazwę, lub kliknąć prawym przyciskiem myszy i wybrać polecenie **Zmień nazwę**lub nacisnąć klawisz **F2** .

   Jeśli chcesz zmienić nazwy odwołań do pliku, może pojawić się monit `Class1` . Nie ma znaczenia, jak odpowiadasz, ponieważ zamieniasz kod w przyszłości.

1. Teraz musimy dodać odwołanie do projektu, aby pierwszy projekt mógł używać interfejsów API udostępnianych przez nową bibliotekę klas.  Kliknij prawym przyciskiem myszy węzeł **odwołania** w pierwszym projekcie i wybierz polecenie **Dodaj odwołanie do projektu**.

   ![Zrzut ekranu przedstawiający element menu Dodaj odwołanie do projektu](media/vs-2019/calculator2-add-project-reference-dark.png)

   Zostanie wyświetlone okno dialogowe **Menedżer odwołań** . To okno dialogowe pozwala dodawać odwołania do innych projektów, jak również zestawy i biblioteki DLL modelu COM wymagane przez projekty.

   ![Zrzut ekranu przedstawiający okno dialogowe Menedżer odwołań](media/vs-2019/calculator2-ref-manager-dark.png)

1. W oknie dialogowym **Menedżer odwołań** zaznacz pole wyboru dla projektu **CalculatorLibrary** , a następnie wybierz **przycisk OK**.  Odwołanie do projektu jest wyświetlane w węźle **projekty** w **Eksplorator rozwiązań**.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z odwołaniem do projektu](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. W *program.cs*wybierz `Calculator` klasę i cały jej kod, a następnie naciśnij **klawisze Ctrl + X** , aby wyciąć ją z program.cs. Następnie w **CalculatorLibrary**, w *CalculatorLibrary.cs*, wklej kod do `CalculatorLibrary` przestrzeni nazw. Następnie zmień klasę kalkulator, `public` Aby uwidocznić ją poza biblioteką. Kod w *CalculatorLibrary.cs* powinien teraz wyglądać podobnie do następującego kodu:

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

1. Pierwszy projekt zawiera odwołanie, ale zobaczysz błąd, że wywołanie Kalkulator. DoOperation nie jest rozpoznawane. Wynika to z faktu, że CalculatorLibrary znajduje się w przestrzeni nazw różnic, więc Dodaj `CalculatorLibrary` przestrzeń nazw dla w pełni kwalifikowanego odwołania.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Zamiast tego spróbuj dodać dyrektywę using na początku pliku:

   ```csharp
   using CalculatorLibrary;
   ```

   Ta zmiana powinna pozwolić na usunięcie przestrzeni nazw CalculatorLibrary z witryny wywołania, ale istnieje teraz niejednoznaczność. Czy `Calculator` Klasa jest w CalculatorLibrary, czy jest kalkulatorem przestrzeni nazw?  Aby usunąć niejednoznaczność, Zmień nazwę przestrzeni nazw `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Dokumentacja bibliotek platformy .NET: zapisywanie w dzienniku

1. Załóżmy, że chcesz teraz dodać dziennik wszystkich operacji i zapisać go w pliku tekstowym. Klasa platformy .NET `Trace` udostępnia tę funkcję. (Przydatne jest również w przypadku podstawowych technik debugowania drukowania).  Klasa śledzenia znajduje się w System. Diagnostics, więc Zacznij od dodania dyrektywy using:

   ```csharp
   using System.Diagnostics;
   ```

1. Analizując sposób używania klasy śledzenia, należy przytrzymać na odwołanie do klasy, która jest skojarzona z FILESTREAM. Oznacza to, że kalkulator będzie działał lepiej jako obiekt, więc dodamy Konstruktor.

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

1. I musimy zmienić metodę statyczną `DoOperation` w metodę elementu członkowskiego.  Dodajmy również dane wyjściowe do każdego obliczenia dla dziennika, tak aby DoOperation wyglądać następująco:

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

1. Teraz z powrotem w Program.cs, wywołanie statyczne jest oflagowane czerwoną falistej. Aby rozwiązać ten problem, należy utworzyć `calculator` zmienną, dodając następujący wiersz tuż przed pętlą while:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   I zmodyfikuj witrynę wywołania w `DoOperation` następujący sposób:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Ponownie uruchom program, a następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz folder w Eksploratorze plików**, a następnie przejdź w dół w Eksploratorze plików do folderu danych wyjściowych. Może to być plik *bin/debug/netcoreapp 3.1*, a następnie *otworzyć go.*

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Dodaj pakiet NuGet: Zapisz do pliku JSON

1. Teraz Załóżmy, że chcemy wyprowadzać operacje w formacie JSON, popularnym i przenośnym formacie do przechowywania danych obiektu. Aby zaimplementować tę funkcję, należy odwołać się do pakietu NuGet Newtonsoft.Jsw systemie. Pakiety NuGet są głównym pojazdem do dystrybucji bibliotek klas .NET. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu CalculatorLibrary, a następnie wybierz polecenie **Zarządzaj pakietami NuGet**.

   ![Zrzut ekranu przedstawiający zarządzanie pakietami NuGet w menu skrótów](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Zostanie otwarty Menedżer pakietów NuGet.

   ![Zrzut ekranu Menedżera pakietów NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Wyszukaj Newtonsoft.Jsw pakiecie i wybierz pozycję **Zainstaluj**.

   ![Zrzut ekranu przedstawiający informacje o pakiecie NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Pakiet zostanie pobrany i dodany do projektu, a nowy wpis zostanie wyświetlony w węźle odwołania w **Eksplorator rozwiązań**.

1. Dodaj dyrektywę using dla Newtonsoft.Jsw pakiecie na początku *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Teraz Zastąp Konstruktor kalkulatorem przy użyciu następującego kodu i Utwórz obiekt elementu członkowskiego JsonWriter:

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

1. Zmodyfikuj `DoOperation` metodę, aby dodać kod modułu zapisywania JSON:

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

1. Musisz dodać metodę, aby zakończyć składnię JSON, gdy użytkownik ukończy wprowadzanie danych operacji.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. I w *program.cs*, Dodaj wywołanie do końca na końcu.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Skompiluj i uruchom aplikację, a po zakończeniu wprowadzania kilku operacji Zamknij aplikację prawidłowo, używając polecenia "n".  Teraz otwórz consolelog.jsw pliku i powinien wyglądać podobnie do poniższego:

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

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka. Aby dowiedzieć się jeszcze więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj pracę z więcej samouczkami w języku C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Kontynuuj pracę z programem Visual Studio IDE — Omówienie](/../visual-studio-ide.md)

## <a name="see-also"></a>Zobacz też

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Informacje o debugowaniu kodu w języku C# w programie Visual Studio](tutorial-debugger.md)
