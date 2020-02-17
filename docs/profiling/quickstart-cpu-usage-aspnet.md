---
title: Analizowanie danych użycia procesora CPU (ASP.NET Core)
description: Mierzenie wydajności aplikacji w aplikacjach ASP.NET Core przy użyciu narzędzia diagnostyki użycia procesora CPU
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 367d789513e8ac220566cb4e451bcea015ec5a2a
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275072"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Szybki Start: analizowanie danych użycia procesora CPU w programie Visual Studio (ASP.NET Core)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. Oto narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego.

System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i Utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

   W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Wizualizacja C#** , a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Web Application (.NET Core)** . Następnie nadaj nazwę projektowi *MyProfilingApp_MVC*.

   > [!NOTE]
   > Jeśli szablon projektu **aplikacji sieci Web ASP.NET (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

   W oknie dialogowym, które się pojawi, wybierz **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *ASP.NET* w polu wyszukiwania. Następnie wybierz **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **aplikacja sieci Web ASP.NET (.NET Core)** , a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli szablon **aplikacji sieci Web ASP.NET (.NET Core)** nie jest widoczny, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie **ASP.NET i programowanie dla sieci Web** .

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyProfilingApp_MVC* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   W wyświetlonym oknie wybierz pozycję **aplikacja sieci Web (Model-View-Controller)** , a następnie wybierz pozycję **Utwórz**.

   ::: moniker-end

   Program Visual Studio otwiera nowy projekt.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder modele i wybierz polecenie dodaj **klasę** > .

1. Nazwij nową klasę `Data.cs` a następnie wybierz pozycję **Dodaj**.

1. W Eksplorator rozwiązań otwórz `Models/Data.cs` i Dodaj następującą instrukcję `using` na początku pliku:

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

   ::: moniker range="vs-2017"

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

    ::: moniker-end
    ::: moniker range="vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    przy użyciu tego kodu:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Krok 1: Zbierania danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w konstruktorze `Simple`:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

1. Następnie ustaw drugi punkt przerwania dla zamykającego nawiasu klamrowego na końcu konstruktora `Simple`:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.

1. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **debuguj** > **Windows** > **Pokaż narzędzia diagnostyczne**.

1. Kliknij pozycję **debuguj** > **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

1. Po zakończeniu ładowania aplikacji kliknij odpowiednie łącze w górnej części strony sieci Web, aby rozpocząć Uruchamianie nowego kodu.

   ::: moniker range="vs-2017"
   W programie Visual Studio 2017 kliknij link **informacje** , aby uruchomić kod.
   ::: moniker-end
   ::: moniker range="vs-2019"
   W programie Visual Studio 2019 kliknij link **prywatność** , aby uruchomić kod.
   ::: moniker-end

1. Zapoznaj się z widokiem **Podsumowanie** narzędzi diagnostycznych.

1. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU przez wybranie opcji **Rejestruj profil procesora**, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Gdy zbieranie danych jest włączone, przycisk Rejestruj wyświetla czerwony okrąg.

     Po wybraniu opcji **Rejestruj profil procesora CPU**program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonywania, a także wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.

     Narzędzie użycie procesora CPU wyświetla raport na karcie **użycie procesora CPU** .

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji kliknij dwukrotnie funkcję `MyProfilingApp_MVC.Models.ServerClass::GetNumber`.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywołujący/wywoływany narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** (`ServerClass::GetNumber`w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w obszarze **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (Na tym rysunku 2220 z 2235 MS były spędzane w treści funkcji, a pozostały czas (< 20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizuj użycie pamięci](../profiling/memory-usage.md), aby zidentyfikować wąskie gardła wydajności.
- [Analizuj użycie procesora](../profiling/cpu-usage.md) , aby uzyskać bardziej szczegółowe informacje o narzędziu Użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
