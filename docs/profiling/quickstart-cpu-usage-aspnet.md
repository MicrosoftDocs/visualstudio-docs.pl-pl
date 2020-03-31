---
title: Analizowanie danych użycia procesora (ASP.NET Core)
description: Mierzenie wydajności aplikacji w aplikacjach ASP.NET Core za pomocą narzędzia diagnostycznego użycie procesora CPU
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
ms.openlocfilehash: f79a9f5178959b9a1ec79dc3c22d8da9c0f6735e
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80411976"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Szybki start: analizowanie danych użycia procesora w programie Visual Studio (ASP.NET Core)

Visual Studio zawiera wiele zaawansowanych funkcji, które ułatwią analizowanie problemów z wydajnością w aplikacji. W tym temacie przedstawiono szybki sposób, aby dowiedzieć się niektóre z podstawowych funkcji. W tym miejscu przyjrzymy się narzędziu do identyfikacji wąskich gardeł wydajności ze względu na wysokie użycie procesora CPU. Narzędzia diagnostyczne są obsługiwane dla rozwoju platformy .NET w programie Visual Studio, w tym ASP.NET i rozwoju macierzystego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesją diagnostyczną. Jeśli narzędzie **użycia procesora CPU** opisane w tym miejscu nie daje danych, które są potrzebne, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla Ciebie. W wielu przypadkach wąskie gardło wydajności aplikacji może być spowodowane przez coś innego niż procesor, takich jak pamięć, renderowanie interfejsu użytkownika lub czas żądania sieci. [PerfTips](../profiling/perftips.md), innego narzędzia profilowania zintegrowanego z debugerem, pozwala również na krok przez kod i zidentyfikować, jak długo trwa określone funkcje lub bloki kodu, aby zakończyć.

System Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (okno**Narzędzia diagnostyczne).** W systemie Windows 7 lub nowszym można użyć narzędzia pośmiertnego, [profilera wydajności](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

   W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET aplikacji sieci Web (.NET Core)**. Następnie nazwij projekt *MyProfilingApp_MVC*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **ASP.NET aplikacji sieci Web (NET Core),** wybierz łącze Otwórz Instalator programu Visual **Studio** w lewym okienku okna dialogowego **Nowy projekt.** Uruchamia instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

   W wyświetlonym oknie dialogowym wybierz pozycję **MVC** w środkowym okienku, a następnie kliknij przycisk **OK**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Jeśli okno startowe nie jest otwarte, wybierz polecenie **Okno startowe** **pliku** > .

   W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Utwórz nowy projekt** wprowadź lub wpisz *asp.net* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **ASP.NET aplikacji sieci Web (.NET Core),** a następnie wybierz pozycję **Dalej**.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET aplikacji sieci Web (.NET Core),** można go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features** Następnie w Instalatorze programu Visual Studio wybierz ASP.NET i obciążenia **tworzenia sieci Web.**

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyProfilingApp_MVC* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   W wyświetlonym oknie wybierz pozycję **Aplikacja sieci Web (Model-View-Controller),** a następnie wybierz pozycję **Utwórz**.

   ::: moniker-end

   Visual Studio otwiera nowy projekt.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy folder Modele i wybierz polecenie **Dodaj** > **klasę**.

1. Nazwij `Data.cs` nową klasę i wybierz pozycję **Dodaj**.

1. W Eksploratorze rozwiązań otwórz `Models/Data.cs` i dodaj następującą `using` instrukcję do górnej części pliku:

    ```csharp
    using System.Threading;
    ```

1. W Data.cs zastąp następujący kod:

    ```csharp
    public class Data
    {
    }
    ```

    z tym kodem:

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

1. W Eksploratorze rozwiązań otwórz *plik Controller/HomeControllers.cs*i zastąp następujący kod:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    z tym kodem:

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

    z tym kodem:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Krok 1: Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym `Simple` wierszu kodu w konstruktorze:

    `for (int i = 0; i < 200; i++)`

    Ustaw punkt przerwania, klikając w marginesie wiersza kodu.

1. Następnie ustaw drugi punkt przerwania na nawiasie klamrowym zamknięcia na końcu konstruktora: `Simple`

     ![Ustawianie punktów przerwania profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które chcesz analizować.

1. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij przycisk **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show .

1. Kliknij **przycisk Debugowanie** > **rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

1. Po zakończeniu ładowania aplikacji kliknij odpowiednie łącze u góry strony sieci web, aby rozpocząć uruchamianie nowego kodu.

   ::: moniker range="vs-2017"
   W programie Visual Studio 2017 kliknij łącze **Informacje,** aby uruchomić kod.
   ::: moniker-end
   ::: moniker range="vs-2019"
   W programie Visual Studio 2019 kliknij łącze **Prywatność,** aby uruchomić kod.
   ::: moniker-end

1. Spójrz na **widok Podsumowanie** narzędzi diagnostycznych.

1. Gdy debuger jest wstrzymany, włącz zbieranie danych użycia procesora CPU, wybierając pozycję **Record CPU Profile**, a następnie otwórz kartę Użycie **procesora CPU.**

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora](../profiling/media/quickstart-cpu-usage-summary.png)

     Gdy zbieranie danych jest włączone, przycisk nagrywania wyświetla czerwone kółko.

     Po **wybraniu opcji Zarejestruj profil procesora CPU**program Visual Studio rozpocznie rejestrowanie funkcji i czasu ich wykonania, a także udostępni wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Można wyświetlić te dane zbierane tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane dotyczące wydajności dla aplikacji specjalnie dla regionu kodu, który działa między dwoma punktami przerwania.

     Profiler rozpoczyna przygotowywanie danych wątku. Poczekaj, aż się skończy.

     Narzędzie Użycie procesora CPU wyświetla raport na karcie **Użycie procesora CPU.**

     W tym momencie można rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analizowanie danych użycia procesora

Zaleca się rozpoczęcie analizowania danych przez zbadanie listy funkcji w obszarze Użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy, a następnie przyjrzenie się każdej z nich.

1. Na liście funkcji sprawdź funkcje, które wykonują najwięcej pracy.

     ![Karta Użycie procesora CPU narzędzia diagnostyczne](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkcje są wyświetlane w kolejności, począwszy od tych, którzy wykonują najwięcej pracy (nie są one w kolejności wywołania). Pomaga to szybko zidentyfikować najdłużej działające funkcje.

2. Na liście funkcji kliknij dwukrotnie `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji w lewym okienku zostanie otwarty widok **Wywołujący/Wywoływany.**

    ![Narzędzia diagnostyczne Widok wywołujący/wywoływany](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku`ServerClass::GetNumber`i w polu **Bieżąca funkcja** ( , w tym przykładzie). Funkcja, która wywoływała bieżącą funkcję, jest wyświetlana po lewej stronie w obszarze **Funkcja wywoływania,** a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **Wywoływane funkcje** po prawej stronie. (Można wybrać do któregokolwiek z pól, aby zmienić bieżącą funkcję).

    Ten widok pokazuje całkowity czas (ms) i procent całkowitego czasu działania aplikacji, który został pobrany do wykonania.

    **Treść funkcji** pokazuje również całkowitą ilość czasu (i procent czasu) spędzoną w treści funkcji, z wyłączeniem czasu spędzonego podczas wywoływania i wywoływania funkcji. (Na tej ilustracji 2220 z 2235 ms zostało spędzonych w treści funkcji, a pozostały czas (<20 ms) został spędzony w kodzie zewnętrznym wywołanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Wysokie wartości w **treści funkcji** może wskazywać wąskie gardło wydajności w ramach samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)w celu zidentyfikowania wąskich gardeł wydajności.
- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md) w celu uzyskania bardziej szczegółowych informacji na temat narzędzia użycia procesora CPU.
- Analizowanie użycia procesora bez dołączonego debugera lub kierowanie na działającą aplikację — aby uzyskać więcej informacji, zobacz [Zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [programie Run profilowanie narzędzi z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
