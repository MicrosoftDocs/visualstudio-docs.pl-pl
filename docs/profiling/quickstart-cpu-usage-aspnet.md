---
title: Analizowanie danych użycia procesora CPU (ASP.NET)
description: Mierzyć wydajność aplikacji w aplikacji ASP.NET przy użyciu narzędzia do diagnostyki użycia procesora CPU
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
ms.openlocfilehash: 2026767778f1e060ccff4a05af2649a40c1d984f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810263"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Szybki start: Analizowanie danych użycia procesora CPU w Visual Studio (ASP.NET)

Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w analizie problemów z wydajnością w aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji. W tym miejscu przyjrzymy się narzędziem do identyfikowania wąskich gardeł wydajności ze względu na wysokie użycie procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisane w tym miejscu nie umożliwiają danych, których potrzebują, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego.

Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno). Windows 7 lub nowszy, można użyć narzędzia do późniejszej analizy [Profiler wydajności](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)**.

    Jeśli nie widzisz **aplikacji sieci Web ASP.NET** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, wybierz **Modyfikuj**.

1. Wpisz nazwę, takich jak **MyProfilingApp_MVC** i kliknij przycisk **OK**.

1. W oknie dialogowym wybierz **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt. Eksplorator rozwiązań (w okienku po prawej stronie) pokazuje plików projektu.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy folderu modeli, a następnie wybierz **Dodaj** > **klasy**.

1. Nadaj nowej klasie `Data.cs` i wybierz polecenie **Dodaj**.

1. W Eksploratorze rozwiązań Otwórz `Models/Data.cs` i dodaj następującą `using` instrukcji na górze pliku:

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

1. W Eksploratorze rozwiązań Otwórz *Controller/HomeControllers.cs*i Zastąp następujący kod:

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

1. Najpierw ustaw punkt przerwania w swojej aplikacji, w tym wierszu kodu w `Simple` Konstruktor:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając na marginesie po lewej stronie wiersza kodu.

1. Następnym etapem jest skonfigurowanie drugiego punktu przerwania na zamykającego nawiasu klamrowego na końcu `Simple` Konstruktor:

     ![Ustawianie punktów przerwania do profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.

1. **Narzędzia diagnostyczne** okna jest jeszcze widoczny, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

1. Kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

1. Po zakończeniu ładowania aplikacji kliknij przycisk **o** link u góry strony sieci web, aby rozpocząć Uruchamianie nowego kodu.

1. Przyjrzyj się **Podsumowanie** zostanie wyświetlony widok narzędzia diagnostyczne.

1. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU, wybierając **profil procesora CPU rekordu**, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyczne Włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Po włączeniu funkcji zbierania danych, przycisk Nagraj wyświetla czerwone kółko.

     Po wybraniu **profil procesora CPU rekordu**, Visual Studio spowoduje rozpoczęcie rejestrowania funkcji i czas, jaki przyjmują do wykonania, a także zawiera wykres osi czasu, można użyć, aby skoncentrować się na poszczególnych segmentach sesji pobierania próbek. Ta zebrane dane może wyświetlać tylko w przypadku, gdy aplikacja jest zatrzymywane w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.

     Narzędzie użycie procesora CPU wyświetla raport w **użycie procesora CPU** kartę.

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

     ![Karta użycia narzędzia Procesora diagnostyki](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji dwukrotnie kliknij `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** w okienku po lewej stronie zostanie otwarty widok.

    ![Widok wywołujący/wywoływany narzędzia do diagnostyki](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybranej funkcji pojawia się w nagłówku i w **bieżącą funkcję** pole (`ServerClass::GetNumber`, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, oraz wszelkie funkcje wywołane przez bieżącą funkcję są pokazane w **funkcji o nazwie** pole po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Funkcja treści** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. (Na tej ilustracji 2220 poza 2235 ms spędzono w treści funkcji i pozostały czas (< 20 ms) był poświęcony w kodzie zewnętrznych wywoływanych przez tę funkcję). Rzeczywiste wartości może się różnić w zależności od środowiska.

    > [!TIP]
    > O wysokiej wartości w **treści funkcji** może wskazać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do identyfikowania wąskich gardeł wydajności.
- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md) uzyskać bardziej szczegółowe informacje na temat narzędzia użycie procesora CPU.
- Analizowanie użycia procesora CPU bez debugera dołączone lub stosując uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
