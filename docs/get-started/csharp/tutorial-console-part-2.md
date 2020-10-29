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
ms.openlocfilehash: 4f2d5bf573da940c39790d6868a94d588e5efb7b
ms.sourcegitcommit: ae9145b32fc8e1e663e504c315a5df5dd302fee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2020
ms.locfileid: "92918216"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Samouczek: zwiększanie prostej aplikacji konsolowej w języku C#

W tym samouczku dowiesz się, jak za pomocą programu Visual Studio zwiększyć aplikację konsolową utworzoną w pierwszej części. Poznasz niektóre funkcje programu Visual Studio, które będą potrzebne do codziennego opracowywania, na przykład zarządzanie wieloma projektami i odwoływanie się do pakietów innych firm.

Po ukończeniu [pierwszej części](tutorial-console.md) tej serii masz już aplikację konsolową Kalkulator.  Aby pominąć część 1, możesz zacząć od otwarcia projektu z repozytorium GitHub. Aplikacja kalkulatora języka C# znajduje się w [repozytorium vs-samouczek-przykłady](https://github.com/MicrosoftDocs/vs-tutorial-samples), więc możesz wykonać kroki opisane w [samouczku: Otwórz projekt z repozytorium](../tutorial-open-project-from-repo.md) , aby rozpocząć pracę.

## <a name="add-a-new-project"></a>Dodaj nowy projekt

Kod w języku rzeczywistym obejmuje wiele projektów współpracujących w rozwiązaniu. Teraz Dodajmy kolejny projekt do aplikacji Kalkulator. Będzie to Biblioteka klas, która udostępnia niektóre funkcje kalkulatora.

1. W programie Visual Studio można użyć pliku polecenia menu najwyższego poziomu **File**  >  **Dodaj**  >  **Nowy projekt** , aby dodać nowy projekt, ale można również kliknąć prawym przyciskiem myszy istniejącą nazwę projektu (nazywaną "węzłem projektu") i otworzyć menu skrótów projektu (lub menu kontekstowe). To menu skrótów zawiera wiele sposobów dodawania funkcjonalności do projektów. W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt** .

1. Wybierz bibliotekę klas szablonu projektu C# **(.NET standard)** .

   ![Zrzut ekranu przedstawiający wybór szablonu projektu biblioteki klas](media/vs-2019/calculator2-add-project-dark.png)

1. Wpisz nazwę projektu **CalculatorLibrary** , a następnie wybierz pozycję **Utwórz** . Program Visual Studio tworzy nowy projekt i dodaje go do rozwiązania.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dodanym projektem biblioteki klas CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Zamiast *Class1.cs* należy zmienić nazwę pliku **CalculatorLibrary.cs** . Możesz kliknąć nazwę w **Eksplorator rozwiązań** , aby zmienić jej nazwę, lub kliknąć prawym przyciskiem myszy i wybrać polecenie **Zmień nazwę** lub nacisnąć klawisz **F2** .

   Jeśli chcesz zmienić nazwy odwołań do pliku, może pojawić się monit `Class1` . Nie ma znaczenia, jak odpowiadasz, ponieważ zamieniasz kod w przyszłości.

1. Teraz musimy dodać odwołanie do projektu, aby pierwszy projekt mógł używać interfejsów API udostępnianych przez nową bibliotekę klas.  Kliknij prawym przyciskiem myszy węzeł **odwołania** w pierwszym projekcie i wybierz polecenie **Dodaj odwołanie do projektu** .

   ![Zrzut ekranu przedstawiający element menu Dodaj odwołanie do projektu](media/vs-2019/calculator2-add-project-reference-dark.png)

   Zostanie wyświetlone okno dialogowe **Menedżer odwołań** . To okno dialogowe pozwala dodawać odwołania do innych projektów, jak również zestawy i biblioteki DLL modelu COM wymagane przez projekty.

   ![Zrzut ekranu przedstawiający okno dialogowe Menedżer odwołań](media/vs-2019/calculator2-ref-manager-dark.png)

1. W oknie dialogowym **Menedżer odwołań** zaznacz pole wyboru dla projektu **CalculatorLibrary** , a następnie wybierz **przycisk OK** .  Odwołanie do projektu jest wyświetlane w węźle **projekty** w **Eksplorator rozwiązań** .

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z odwołaniem do projektu](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. W *program.cs* wybierz `Calculator` klasę i cały jej kod, a następnie naciśnij **klawisze Ctrl + X** , aby wyciąć ją z program.cs. Następnie w **CalculatorLibrary** , w *CalculatorLibrary.cs* , wklej kod do `CalculatorLibrary` przestrzeni nazw. Następnie zmień klasę kalkulator, `public` Aby uwidocznić ją poza biblioteką. Kod w *CalculatorLibrary.cs* powinien teraz wyglądać podobnie do następującego kodu:

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

1. Załóżmy, że chcesz teraz dodać dziennik wszystkich operacji i zapisać go w pliku tekstowym. Klasa platformy .NET `Trace` udostępnia tę funkcję. (Przydatne jest również w przypadku podstawowych technik debugowania drukowania).  Klasa śledzenia znajduje się w System. Diagnostics, a wymagane są klasy System.IO `StreamWriter` , więc Zacznij od dodania dyrektyw using:

   ```csharp
   using System.IO;
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

1. Ponownie uruchom program, a następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz folder w Eksploratorze plików** , a następnie przejdź w dół w Eksploratorze plików do folderu danych wyjściowych. Może to być plik *bin/debug/netcoreapp 3.1* , a następnie *otworzyć go.*

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Dodaj pakiet NuGet: Zapisz do pliku JSON

1. Teraz Załóżmy, że chcemy wyprowadzać operacje w formacie JSON, popularnym i przenośnym formacie do przechowywania danych obiektu. Aby zaimplementować tę funkcję, należy odwołać się do pakietu NuGet Newtonsoft.Jsw systemie. Pakiety NuGet są głównym pojazdem do dystrybucji bibliotek klas .NET. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu CalculatorLibrary, a następnie wybierz polecenie **Zarządzaj pakietami NuGet** .

   ![Zrzut ekranu przedstawiający zarządzanie pakietami NuGet w menu skrótów](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Zostanie otwarty Menedżer pakietów NuGet.

   ![Zrzut ekranu Menedżera pakietów NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Wyszukaj Newtonsoft.Jsw pakiecie i wybierz pozycję **Zainstaluj** .

   ![Zrzut ekranu przedstawiający informacje o pakiecie NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Pakiet zostanie pobrany i dodany do projektu, a nowy wpis zostanie wyświetlony w węźle odwołania w **Eksplorator rozwiązań** .

1. Dodaj dyrektywę using dla System.IO i Newtonsoft.Jsw pakiecie na początku *CalculatorLibrary.cs* .

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

1. I w *program.cs* , Dodaj wywołanie do końca na końcu.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Skompiluj i uruchom aplikację, a po zakończeniu wprowadzania kilku operacji Zamknij aplikację prawidłowo, używając polecenia "n".  Teraz otwórz calculatorlog.jsw pliku i powinien wyglądać podobnie do poniższego:

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

## <a name="debug-set-and-hit-a-breakpoint"></a>Debuguj: Ustaw i naciśnij punkt przerwania

Debuger programu Visual Studio to zaawansowane narzędzie, które umożliwia uruchamianie kodu krok po kroku, aby znaleźć dokładne miejsce, w którym nadano błąd programistyczny. Następnie można zrozumieć, jakie korekty należy wprowadzić w kodzie. Program Visual Studio umożliwia wykonywanie tymczasowych zmian, dzięki czemu można kontynuować uruchamianie programu.

1. W *program.cs* kliknij margines po lewej stronie poniższego kodu (lub Otwórz menu skrótów i wybierz **punkt przerwania**  >  **Wstaw punkt przerwania** lub naciśnij klawisz **F9** ):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Czerwony okrąg wskazuje punkt przerwania. Możesz użyć punktów przerwania, aby wstrzymywać aplikację i sprawdzać kod. Punkt przerwania można ustawić dla dowolnego wykonywalnego wiersza kodu.

   ![Zrzut ekranu przedstawiający Ustawianie punktu przerwania](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Skompiluj i uruchom aplikację.

1. W uruchomionej aplikacji wpisz niektóre wartości dla obliczenia:

   - Dla pierwszej liczby wpisz **8** i wprowadź ją.
   - Dla drugiej liczby wpisz **0** i wprowadź ją.
   - Na potrzeby operatora Przyjrzyjmy się pewnej zabawy. Wpisz **d** i wprowadź go.

   Aplikacja zawiesza się, gdzie został utworzony punkt przerwania, który jest wskazywany przez żółty wskaźnik po lewej stronie i wyróżniony kod. Wyróżniony kod nie został jeszcze wykonany.

   ![Zrzut ekranu przedstawiający naciśnięcie punktu przerwania](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Teraz, gdy aplikacja jest zawieszona, można sprawdzić stan aplikacji.

## <a name="debug-view-variables"></a>Debuguj: Wyświetl zmienne

1. W wyróżnionym kodzie Umieść kursor nad zmiennymi, takimi jak `cleanNum1` i `op` . Zostaną wyświetlone bieżące wartości tych zmiennych ( `8` `d` odpowiednio), które są wyświetlane w etykietkach danych.

   ![Zrzut ekranu przedstawiający wyświetlanie etykietki danych](media/vs-2019/calculator-2-debug-view-datatip.png)

   Podczas debugowania Sprawdź, czy zmienne przechowują wartości, które powinny być przechowywane, są często krytyczne do rozwiązywania problemów.

2. W dolnym okienku Przyjrzyj się oknom **lokalnym** . (Jeśli jest zamknięty, wybierz **Debuguj**  >  **System Windows**  >  Elementy **lokalne** , aby je otworzyć.

   W oknie zmiennych lokalnych zobaczysz każdą zmienną, która jest obecnie w zakresie wraz z jej wartością i typem.

   ![Zrzut ekranu okna zmiennych lokalnych](media/vs-2019/calculator-2-debug-locals-window.png)

3. Zapoznaj się z oknem **Autokorekty** .

   Okno automatycznie jest podobne do okna zmiennych **lokalnych** , ale pokazuje zmienne bezpośrednio poprzedzające i po bieżącym wierszu kodu, w którym aplikacja jest wstrzymana.

   Następnie można wykonać kod w debugerze po jednej instrukcji, która jest nazywana *krokowe* .

## <a name="debug-step-through-code"></a>Debugowanie: przechodzenie przez kod

1. Naciśnij klawisz **F11** (lub **Debuguj**  >  **krok do** ).

   Za pomocą krok do polecenia aplikacja wykonuje bieżącą instrukcję i przechodzi do następnej instrukcji wykonywalnej (zwykle w następnym wierszu kodu). Żółty wskaźnik po lewej stronie zawsze wskazuje bieżącą instrukcję.

   ![Zrzut ekranu przedstawiający krok do polecenia](media/vs-2019/calculator-2-debug-step-into.png)

   Właśnie przeniesionomy się do `DoOperation` metody w `Calculator` klasie.

1. Aby uzyskać hierarchiczny wygląd przepływu programu, zapoznaj się z oknem **stosu wywołań** . (Jeśli jest zamknięty, wybierz **Debuguj**  >  **System Windows**  >  **Stos wywołań** .)

   ![Zrzut ekranu przedstawiający stos wywołań](media/vs-2019/calculator-2-debug-call-stack.png)

   Ten widok przedstawia bieżącą `Calculator.DoOperation` metodę, wskazywaną przez żółty wskaźnik, a drugi wiersz zawiera funkcję, która ją wywołała, z `Main` metody w *program.cs* . Okno **stos wywołań** pokazuje kolejność, w której metody i funkcje są wywoływane. Ponadto zapewnia dostęp do wielu funkcji debugera, takich jak **Przejdź do kodu źródłowego** , z menu skrótów.

1. Naciśnij klawisz **F10** (lub **Debuguj**  >  **krokowo** ), dopóki aplikacja nie zatrzyma się na `switch` instrukcji.

   ```csharp
   switch (op)
   {
   ```

   Krok nad poleceniem jest podobny do kroku do polecenia, z tą różnicą, że jeśli bieżąca instrukcja wywołuje funkcję, debuger uruchamia kod w wywołanej funkcji i nie wstrzymuje wykonywania do momentu, gdy funkcja zwróci wartość. Krok powyżej to szybszy sposób nawigowania po kodzie, jeśli nie interesuje Cię konkretną funkcję.

1. Naciśnij klawisz **F10** jeszcze raz, aby aplikacja zatrzymał się w następującym wierszu kodu.

   ```csharp
   if (num2 != 0)
   {
   ```

   Ten kod sprawdza podzielenie przez zero wielkości liter. Jeśli aplikacja będzie kontynuować, zgłosi ogólny wyjątek (błąd), ale Załóżmy, że Rozważmy tę usterkę i chcesz zrobić coś innego, na przykład wyświetlić rzeczywistą wartość zwróconą w konsoli. Jedną z opcji jest użycie funkcji debugera o nazwie Edit-and-Continue, aby wprowadzić zmiany w kodzie, a następnie kontynuować debugowanie. Jednak zostanie wyświetlona inna lewę, aby tymczasowo zmodyfikować przepływ wykonywania.

## <a name="debug-test-a-temporary-change"></a>Debuguj: testowanie tymczasowej zmiany

1. Wybierz żółty wskaźnik, który jest obecnie wstrzymany w `if (num2 != 0)` instrukcji, i przeciągnij go do poniższej instrukcji.

   ```csharp
   result = num1 / num2;
   ```

   Dzięki temu aplikacja całkowicie pomija `if` instrukcję, więc można zobaczyć, co się dzieje po podzieleniu przez zero.

1. Naciśnij klawisz **F10** , aby wykonać wiersz kodu.

1. Umieść kursor nad `result` zmienną i zobaczysz, że zawiera ona wartość `Infinity` .

   W języku C# `Infinity` jest wynikiem dzielenia przez zero.

1. Naciśnij klawisz **F5** (lub **Debuguj**  >  **Kontynuuj debugowanie** ).

   Symbol nieskończoności jest wyświetlany w konsoli programu jako wynik operacji matematycznej.

1. Zamknij aplikację prawidłowo, używając polecenia "n".

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka. Aby dowiedzieć się jeszcze więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj pracę z więcej samouczkami w języku C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Kontynuuj pracę z programem Visual Studio IDE — Omówienie](/../visual-studio-ide.md)

## <a name="see-also"></a>Zobacz także

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Informacje o debugowaniu kodu w języku C# w programie Visual Studio](tutorial-debugger.md)
