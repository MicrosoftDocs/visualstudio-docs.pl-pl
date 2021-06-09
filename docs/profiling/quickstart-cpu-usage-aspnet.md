---
title: Analizowanie danych użycia procesora CPU (ASP.NET Core)
description: Mierzenie wydajności aplikacji w ASP.NET Core przy użyciu narzędzia diagnostycznego Użycie procesora CPU
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
ms.openlocfilehash: aa0c95e3a9f3598cd6399b565adb75faccac22a8
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761150"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Szybki start: analizowanie danych użycia procesora CPU w Visual Studio (ASP.NET Core)

Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób na nauczenia się niektórych podstawowych funkcji. W tym miejscu przyjrzymy się narzędziu do identyfikowania wąskich gardeł wydajności spowodowanych wysokim użyciem procesora CPU. Narzędzia diagnostyczne są obsługiwane na potrzeby programowania na platformie .NET w Visual Studio, w tym ASP.NET, a także w przypadku programowania w języku natywnym/C++.

Centrum diagnostyki oferuje wiele innych opcji uruchamiania sesji diagnostyki i zarządzania nimi. Jeśli narzędzie **Użycie procesora CPU** opisane w tym miejscu nie dostarcza potrzebnych danych, inne narzędzia [profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być dla Ciebie przydatne. W wielu przypadkach wąskie gardło wydajności aplikacji może być spowodowane przez coś innego niż procesor, taki jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. [PerfTips](../profiling/perftips.md), inne narzędzie profilowania zintegrowane z debugerem, umożliwia również krok po kroku kod i określenie, jak długo trwa ukończenie określonych funkcji lub bloków kodu.

Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (**narzędzia diagnostyczne** okno). W systemie Windows 7 lub nowszym można użyć narzędzia post mortem, profiler wydajności [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz Visual Studio i utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

   W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **Visual C#,** a następnie wybierz pozycję **Internet.** W środkowym okienku wybierz **pozycję ASP.NET Web Application (.NET Core).** Następnie nadaj *projektowi nazwę MyProfilingApp_MVC*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **ASP.NET Web Application (.NET Core),** wybierz link **Otwórz** Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

   W wyświetlonym oknie dialogowym wybierz **pozycję MVC** w środkowym okienku, a następnie kliknij przycisk **OK.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   W Visual Studio 2019 r. wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję **Okno**  >  **uruchamiania pliku,** a następnie wybierz pozycję **Utwórz nowy projekt.**

   Wpisz **aplikację internetową w** polu wyszukiwania, wybierz język **C#,** wybierz pozycję **ASP.NET Core Web Application (Model-View-Controller), a** następnie wybierz pozycję **Dalej.** Na następnym ekranie nadaj *projektowi nazwę MyProfilingApp_MVC*, a następnie wybierz pozycję **Dalej.**

   Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**

   > [!NOTE]
   > Jeśli szablon aplikacji internetowej **ASP.NET (.NET Core)** nie jest wyświetlony, możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji. Następnie w witrynie Instalator programu Visual Studio wybierz obciążenie **Tworzenie aplikacji ASP.NET sieci Web.**
   ::: moniker-end

   Visual Studio tworzy i otwiera nowy projekt.

1. W Eksplorator rozwiązań prawym przyciskiem myszy folder Modele i wybierz polecenie **Dodaj**  >  **klasę**.

1. Nadaj nowej klasie nazwę `Data.cs` i wybierz pozycję **Dodaj**.

1. W Eksplorator rozwiązań otwórz plik i dodaj następującą instrukcje `Models/Data.cs` `using` na początku pliku:

    ```csharp
    using System.Threading;
    ```

1. W kodzie Data.cs zastąp następujący kod:

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

1. W Eksplorator rozwiązań otwórz *kontroler/HomeControllers.cs* i zastąp następujący kod:

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
    ::: moniker range=">=vs-2019"

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


## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `Simple` konstruktorze:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając utter z lewej strony wiersza kodu.

1. Następnie ustaw drugi punkt przerwania w zamykającym nawiasie klamrowy na końcu `Simple` konstruktora:

     ![Ustawianie punktów przerwania na czas profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Ustawiając dwa punkty przerwania, możesz ograniczyć zbieranie danych do części kodu, które chcesz analizować.

1. Okno **narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję  >  **Debuguj okna**  >  **Pokaż narzędzia diagnostyczne**.

1. Kliknij **pozycję**  >  **Debuguj rozpocznij debugowanie** (lub **Uruchom** na pasku narzędzi lub naciśnij **klawisz F5).**

1. Po zakończeniu ładowania aplikacji kliknij odpowiedni link w górnej części strony internetowej, aby rozpocząć uruchamianie nowego kodu.

   ::: moniker range="vs-2017"
   W Visual Studio 2017 kliknij link **Informacje,** aby uruchomić kod.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   W Visual Studio 2019 r. kliknij link **Prywatność,** aby uruchomić kod.
   ::: moniker-end

1. Przyjrzyj się **widokowi Podsumowanie** narzędzi diagnostycznych.

1. Gdy debuger jest wstrzymany, włącz zbieranie danych użycia procesora CPU, wybierając pozycję Rejestruj profil **procesora CPU,** a następnie otwórz **kartę Użycie procesora** CPU.

     ![Narzędzia diagnostyczne włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Po włączeniu zbierania danych przycisk rekordu wyświetla czerwone kółko.

     Po wybraniu opcji Rejestruj profil **procesora CPU** program Visual Studio rozpocznie rejestrowanie funkcji i czasu ich wykonywania, a także udostępnia wykres osi czasu, za pomocą którym można skoncentrować się na określonych segmentach sesji próbkowania. Zebrane dane można wyświetlić tylko wtedy, gdy aplikacja zostanie zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację do drugiego punktu przerwania.

     Teraz masz dane wydajności dla aplikacji przeznaczone specjalnie dla regionu kodu uruchamianego między dwoma punktami przerwania.

     Profiler rozpoczyna przygotowywanie danych wątku. Poczekaj na zakończenie.

     Narzędzie Użycie procesora CPU wyświetla raport na karcie **Użycie procesora** CPU.

     W tym momencie możesz rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych od zbadania listy funkcji w obszarze Użycie procesora CPU, zidentyfikowania funkcji wykonujących największe zadania, a następnie bliższego przyjrzenia się każdej z nich.

1. Na liście funkcji sprawdź funkcje, które działają najlepiej.

     ![Karta Użycie procesora CPU w narzędziach diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wyświetlane w kolejności rozpoczynającej się od tych, które pracują najlepiej (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłużej działające funkcje.

2. Na liście funkcji kliknij dwukrotnie `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji widok **wywołujący/wywołujący/wywołujący** zostanie otwarty w okienku po lewej stronie.

    ![Widok wywołujący/wywołujący narzędzia diagnostyczne](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w polu **Bieżąca funkcja** `ServerClass::GetNumber` (, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest wyświetlana po lewej stronie w obszarze **Funkcja** wywołująca , a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **Wywołano** funkcje po prawej stronie. (Możesz wybrać oba pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i procent całkowitego czasu działania aplikacji, który zajęło ukończenie funkcji.

    **Treść funkcji** pokazuje również łączną ilość czasu (i procent czasu) spędzonego w treści funkcji z wyłączeniem czasu spędzonego na wywołaniach i wywołanych funkcjach. (Na tej ilustracji 2220 z 2235 ms zostało spędzonych w treści funkcji, a pozostały czas (<20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Wysokie wartości w treści **funkcji mogą** wskazywać wąskie gardło wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci w](../profiling/memory-usage.md)celu zidentyfikowania wąskich gardeł wydajności.
- [Przeanalizuj](../profiling/cpu-usage.md) użycie procesora CPU, aby uzyskać bardziej szczegółowe informacje na temat narzędzia użycia procesora CPU.
- Przeanalizuj użycie procesora CPU bez dołączonego debugera [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) lub przez skierowanie go do uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz Zbieranie danych profilowania bez debugowania w tece Uruchamianie narzędzi profilowania z [debugerem](../profiling/running-profiling-tools-with-or-without-the-debugger.md)lub bez niego.

## <a name="see-also"></a>Zobacz też

- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
