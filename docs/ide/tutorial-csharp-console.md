---
title: Wprowadzenie do aplikacji konsoli języka C# w programie Visual Studio
titleSuffix: ''
description: Dowiedz się, jak w programie Visual Studio krok po kroku dotyczące tworzenia aplikacji konsolowej C#.
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: d15e22ce80ed7e46eea7ded93bff0af8e82d9ef4
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159883"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Samouczek: Wprowadzenie do aplikacji konsolowej C# w programie Visual Studio

W ramach tego samouczka dla języka C#, użyjesz programu Visual Studio do tworzenia i uruchomisz aplikację konsoli i zapoznaj się z niektórymi funkcjami [środowiska zintegrowanego rozwoju Visual Studio (IDE)](../get-started/visual-studio-ide.md) podczas możesz to zrobić.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji C#. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **C#**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Następnie Nazwij plik *Kalkulator*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Dodaj grupy roboczej (opcjonalnie)

Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablon projektu, możesz ją uzyskać, dodając **programowanie dla wielu platform .NET Core** obciążenia. Można dodać tego obciążenia w jednej z dwóch sposobów, zależności od tego, które aktualizacje programu Visual Studio 2017 są instalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Użyj okna dialogowego Nowy projekt

1. Wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Wybierz łącze Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

## <a name="create-a-c-console-calculator-app"></a>Tworzenie aplikacji "C# Console Kalkulator"

1. Po utworzeniu  **C# aplikację Konsolową**, wpisz lub wklej następujący kod do edytora kodu:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
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
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   Kod, który pojawia się po `static void Main(string[] args)` powinien wyglądać jak poniższy zrzut ekranu:

   ![Edytor kodu, przedstawiający Kalkulator konsoli C#](../ide/media/csharp-console-calculator-code.png)

1. Wybierz **Kalkulator** Aby uruchomić program, lub naciśnij **F5**.

   ![Wybierz przycisk Kalkulator, aby uruchomić aplikację z paska narzędzi](../ide/media/csharp-console-calculator-button.png)

1. Wyświetlanie aplikacji w oknie konsoli. Gdy postępuj zgodnie z monitami, aplikacji powinien wyglądać podobnie do poniższej zrzut ekranu:

    ![Okno konsoli przedstawiający aplikację Kalkulator, która obejmuje monity w przypadku działania, które należy podjąć.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Zamknij aplikację

1. Naciśnij dowolny klawisz, aby zamknąć aplikację kalkulatora.

1. Zamknij **dane wyjściowe** okienko w programie Visual Studio.

   ![Zamknij okienko danych wyjściowych w programie Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi na często zadawane pytania

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkiego aby zaznaczyć kilka podstawowych pojęć.

### <a name="what-is-c"></a>Co to jest C#?

C# to bezpieczny typowo język programowania, który działa w .NET Framework i .NET Core. Za pomocą języka C# można utworzyć Windows aplikacji, aplikacji typu klient serwer, aplikacji baz danych, sieci Web XML usług, rozpowszechnianych komponentów i więcej.

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Program Visual Studio jest zintegrowanego rozwoju pakietu narzędzi zwiększających produktywność dla deweloperów. Go traktować jako program, który służy do tworzenia aplikacji i programów.

### <a name="what-is-a-console-app"></a>Co to jest aplikacją konsoli?

Aplikacja konsoli akceptuje dane wejściowe i wyświetla dane wyjściowe w oknie wiersza polecenia, zwanego również Konsola.

### <a name="what-is-net-core"></a>Co to jest .NET Core?

Platforma .NET core to ewolucyjny następnym krokiem programu .NET Framework. Gdzie programu .NET Framework mogą pozwala na udostępnianie kodu w językach programowania .NET Core dodaje możliwość udostępniania kodu między platformami. Jeszcze lepiej jest "open source".

(.NET Framework i .NET Core zawierają biblioteki, funkcji wbudowanych. Te aktualizacje obejmują również środowisko uruchomieniowe języka wspólnego (CLR), który działa jako maszynę wirtualną, w którym ma być uruchamiany w kodzie.)

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Aby uzyskać jeszcze więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Samouczki języka C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Zobacz także

* [Podstawy języka C# dla początkujących kurs wideo](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
