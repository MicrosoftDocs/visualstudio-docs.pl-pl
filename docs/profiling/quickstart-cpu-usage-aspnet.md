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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: fa8601b6fe625c5cab2aa1f5de8a69f2d550ee2a
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683627"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Szybki Start: analizowanie danych użycia procesora CPU w programie Visual Studio (ASP.NET Core)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. Oto narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne obsługują Programowanie dla platformy .NET w programie Visual Studio, w tym ASP.NET, oraz na potrzeby programowania natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji umożliwiających uruchomienie sesji diagnostycznej i zarządzanie nią. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskie gardła wydajności aplikacji może być spowodowane przez coś innego niż procesor CPU, takich jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. [Funkcja PerfTip](../profiling/perftips.md), inne narzędzie profilowania zintegrowanego debugera, umożliwia również przechodzenie przez kod i określenie, jak długo trwa wykonywanie określonych funkcji lub bloków kodu.

System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno **Narzędzia diagnostyczne** ). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i Utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

   W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Web Application (.NET Core)**. Następnie nadaj nazwę projektowi *MyProfilingApp_MVC*.

   > [!NOTE]
   > Jeśli szablon projektu **aplikacji sieci Web ASP.NET (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

   W oknie dialogowym, które się pojawi, wybierz **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   W programie Visual Studio 2019 wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno startowe nie jest otwarte, wybierz polecenie  >  **okno startowe** plików, a następnie wybierz polecenie **Utwórz nowy projekt**.

   W polu wyszukiwania wpisz ciąg **aplikacja sieci Web** , wybierz pozycję **C#** jako język, wybierz pozycję **ASP.NET Core aplikacja internetowa (Model-View-Controller)**, a następnie wybierz przycisk **dalej**. Na następnym ekranie Nazwij projekt *MyProfilingApp_MVC*, a następnie wybierz **dalej**.

   Wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.

   > [!NOTE]
   > Jeśli szablon **aplikacji sieci Web ASP.NET (.NET Core)** nie jest widoczny, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie **ASP.NET i programowanie dla sieci Web** .
   ::: moniker-end

   Program Visual Studio tworzy i otwiera nowy projekt.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder modele i wybierz polecenie **Dodaj**  >  **klasę**.

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

    następującym:

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

1. W Eksplorator rozwiązań otwórz pozycję *Controller/HomeControllers. cs* i Zastąp następujący kod:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    następującym:

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

    następującym:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Krok 1. zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `Simple` konstruktorze:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

1. Następnie ustaw drugi punkt przerwania dla zamykającego nawiasu klamrowego na końcu `Simple` konstruktora:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które mają być analizowane.

1. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

1. Kliknij pozycję **Debuguj**  >  **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

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

     Po wybraniu opcji **Rejestruj profil procesora CPU** program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonywania, a także wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane wydajności dla aplikacji przeznaczone dla regionu kodu, który jest uruchamiany między dwoma punktami przerwania.

     Profiler rozpoczyna Przygotowywanie danych wątku. Poczekaj na zakończenie.

     Narzędzie użycie procesora CPU wyświetla raport na karcie **użycie procesora CPU** .

     W tym momencie można rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych przez badanie listy funkcji w obszarze użycie procesora CPU, zidentyfikowanie funkcji, które są najbardziej potrzebne, a następnie przeprowadzenie bliższej kontroli nad każdą z nich.

1. Na liście funkcji zapoznaj się z funkcjami, które działają najlepiej.

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wymienione w kolejności rozpoczynającej się od tych, w których są wykonywane najwięcej pracy (nie są w kolejności wywołań). Dzięki temu możesz szybko identyfikować najdłuższe uruchomione funkcje.

2. Na liście funkcji kliknij dwukrotnie `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywołujący/wywoływany narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** ( `ServerClass::GetNumber` w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w obszarze **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (MS) i procent całkowitego czasu działania aplikacji, który wykonał działanie.

    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (Na tym rysunku 2220 z 2235 MS były spędzane w treści funkcji, a pozostały czas (<20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizuj użycie pamięci](../profiling/memory-usage.md), aby zidentyfikować wąskie gardła wydajności.
- [Analizuj użycie procesora](../profiling/cpu-usage.md) , aby uzyskać bardziej szczegółowe informacje o narzędziu Użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
