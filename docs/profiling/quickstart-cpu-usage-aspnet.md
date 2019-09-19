---
title: Analizowanie danych użycia procesora CPU (ASP.NET)
description: Mierzenie wydajności aplikacji w aplikacjach ASP.NET przy użyciu narzędzia diagnostyki użycia procesora CPU
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: cbaaa53fe737761fdd938b7861c371e8e5619acc
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128166"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Szybki start: Analizowanie danych użycia procesora CPU w programie Visual Studio (ASP.NET)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. Oto narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego.

Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio wybierz pozycję **plik** > **Nowy projekt**.

1. W **obszarze C#Wizualizacja** wybierz pozycję **Sieć Web**, a następnie w środkowym okienku wybierz pozycję **ASP.NET Web Application (.NET Framework)** .

    Jeśli szablon projektu **aplikacji sieci Web ASP.NET** nie jest widoczny, kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

1. Wpisz nazwę, taką jak **MyProfilingApp_MVC** , i kliknij przycisk **OK**.

1. W oknie dialogowym, które się pojawi, wybierz **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt. Eksplorator rozwiązań (prawego okienka) pokazuje pliki projektu.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder modele i wybierz polecenie **Dodaj** > **klasę**.

1. Nadaj nazwę nowej klasie `Data.cs` i wybierz pozycję **Dodaj**.

1. W Eksplorator rozwiązań Otwórz `Models/Data.cs` i Dodaj następującą `using` instrukcję na początku pliku:

    ```csharp
    using System.Threading;
    ```

1. W Data.cs Zastąp następujący kod:

    ```csharp
    public class Data
    {
    }
    ```

    przy użyciu tego kodu:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. W Eksplorator rozwiązań otwórz pozycję *Controller/HomeControllers. cs*i Zastąp następujący kod:

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    przy użyciu tego kodu:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `Simple` konstruktorze:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

1. Następnie ustaw drugi punkt przerwania dla zamykającego nawiasu klamrowego na końcu `Simple` konstruktora:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.

1. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

1. Kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

1. Po zakończeniu ładowania aplikacji kliknij link **informacje** w górnej części strony sieci Web, aby rozpocząć Uruchamianie nowego kodu.

1. Zapoznaj się z widokiem **Podsumowanie** narzędzi diagnostycznych.

1. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU przez wybranie opcji **Rejestruj profil procesora**, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Gdy zbieranie danych jest włączone, przycisk Rejestruj wyświetla czerwony okrąg.

     Po wybraniu opcji **Rejestruj profil procesora CPU**program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonywania, a także wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.

     Narzędzie użycie procesora CPU wyświetla raport w **użycie procesora CPU** kartę.

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji kliknij dwukrotnie `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywołujący/wywoływany narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** (`ServerClass::GetNumber`w tym przykładzie). Funkcja, która wywołała bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, oraz wszelkie funkcje wywołane przez bieżącą funkcję są pokazane w **funkcji o nazwie** pole po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Funkcja treści** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. (Na tym rysunku 2220 z 2235 MS były spędzane w treści funkcji, a pozostały czas (< 20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > O wysokiej wartości w **treści funkcji** może wskazać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do identyfikowania wąskich gardeł wydajności.
- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md) uzyskać bardziej szczegółowe informacje na temat narzędzia użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
