---
title: Analizowanie danych użycia procesora CPU (C#, Visual Basic)
description: Mierzenie wydajności aplikacji w języku C# i Visual Basic użyciu narzędzia diagnostycznego Użycie procesora CPU
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
- dotnet
ms.openlocfilehash: 056996782d2b38adb96ee53250cc3ea0c0f75596
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761163"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Szybki start: analizowanie danych użycia procesora CPU w Visual Studio (C#, Visual Basic)

Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób na nauczenia się niektórych podstawowych funkcji. W tym miejscu przyjrzymy się narzędziu, aby zidentyfikować wąskie gardła wydajności spowodowane wysokim użyciem procesora CPU. Narzędzia diagnostyczne są obsługiwane na potrzeby programowania na platformie .NET w Visual Studio, w tym ASP.NET, a także w przypadku programowania w języku natywnym/C++.

Centrum diagnostyki oferuje wiele innych opcji uruchamiania sesji diagnostyki i zarządzania nimi. Jeśli narzędzie **Użycie procesora CPU** opisane w tym miejscu nie dostarcza potrzebnych danych, inne narzędzia [profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być dla Ciebie przydatne. W wielu przypadkach wąskie gardło wydajności aplikacji może być spowodowane przez coś innego niż procesor, taki jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. Ten profiler wydajności oferuje wiele innych opcji do nagrywania i analizowania tego rodzaju danych. [PerfTips](../profiling/perftips.md), inne narzędzie profilowania zintegrowane z debugerem, umożliwia również krok po kroku kod i określenie, jak długo trwa ukończenie określonych funkcji lub bloków kodu.

Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (**narzędzia diagnostyczne** okno). W systemie Windows 7 lub nowszym można użyć narzędzia post mortem, profiler wydajności [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz Visual Studio i utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

   W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **C#** **lub** Visual Basic , a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *projektowi nazwę MyProfilerApp.*

   Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** wybierz link **Otwórz** Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję **Okno** > **uruchamiania pliku.**

   W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   W **oknie Create a new project (Tworzenie** nowego projektu) wprowadź lub wpisz *console* (konsola) w polu wyszukiwania. Następnie wybierz **pozycję C#** **lub Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsoli** dla platformy .NET Core, a następnie wybierz pozycję **Dalej.**

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli,** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji. Następnie w chmurze Instalator programu Visual Studio obciążenie Tworzenie aplikacji dla wielu platform dla **platformy .NET Core.**

   W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *MyProfilerApp* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

   Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**

   ::: moniker-end

   Visual Studio otworzy nowy projekt.

2. Otwórz *program Program.cs* i zastąp cały kod następującym kodem:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
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
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > W Visual Basic upewnij się, że obiekt uruchamiania jest ustawiony na `Sub Main` (**Właściwości**  >  **obiektu uruchamiania**  >  **aplikacji**).

## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `Main` funkcji :

    `for (int i = 0; i < 200; i++)`

    lub, w przypadku Visual Basic:

    `For i As Integer = 0 To 199`

    Ustaw punkt przerwania, klikając utter z lewej strony wiersza kodu.

2. Następnie ustaw drugi punkt przerwania w zamykającym nawiasie klamrowy na końcu `Main` funkcji:

     ![Ustawianie punktów przerwania na czas profilowania](../profiling/media/quickstart-cpu-usage-breakpoints.png "Ustawianie punktów przerwania na czas profilowania")

    Ustawiając dwa punkty przerwania, możesz ograniczyć zbieranie danych do części kodu, które chcesz analizować.

3. Okno **narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję  >  **Debuguj okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Kliknij **pozycję**  >  **Debuguj rozpocznij debugowanie** (lub **Uruchom** na pasku narzędzi lub naciśnij **klawisz F5).**

     Po zakończeniu ładowania aplikacji zostanie **wyświetlony widok** Podsumowanie narzędzi diagnostycznych.

5. Gdy debuger jest wstrzymany, włącz zbieranie danych użycia procesora CPU, wybierając pozycję Rejestruj profil **procesora CPU,** a następnie otwórz **kartę Użycie procesora** CPU.

     ![Narzędzia diagnostyczne włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "Narzędzia diagnostyczne włącz profilowanie procesora CPU")

     Po włączeniu zbierania danych przycisk rekordu wyświetla czerwone kółko.

     Po wybraniu opcji Rejestruj profil **procesora CPU** program Visual Studio rozpocznie rejestrowanie funkcji i czasu ich wykonywania, a także udostępnia wykres osi czasu, za pomocą którym można skoncentrować się na określonych segmentach sesji próbkowania. Zebrane dane można wyświetlić tylko wtedy, gdy aplikacja zostanie zatrzymana w punkcie przerwania.

6. Naciśnij **klawisz F5,** aby uruchomić aplikację do drugiego punktu przerwania.

     Teraz masz dane wydajności dla aplikacji przeznaczone specjalnie dla regionu kodu uruchamianego między dwoma punktami przerwania.

     Profiler rozpoczyna przygotowywanie danych wątku. Poczekaj na zakończenie.

     Narzędzie Użycie procesora CPU wyświetla raport na karcie **Użycie procesora** CPU.

     W tym momencie możesz rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych od zbadania listy funkcji w obszarze Użycie procesora CPU, zidentyfikowania funkcji wykonujących największe zadania, a następnie bliższego przyjrzenia się każdej z nich.

1. Na liście funkcji sprawdź funkcje, które działają najlepiej.

     ![Karta Użycie procesora CPU w narzędziach diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu.png "Karta DiagToolsCPUUsage")

    > [!TIP]
    > Funkcje są wyświetlane w kolejności rozpoczynającej się od tych, które pracują najlepiej (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłużej działające funkcje.

2. Na liście funkcji kliknij dwukrotnie `ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji widok **wywołujący/wywołujący/wywołujący** zostanie otwarty w okienku po lewej stronie.

    ![Widok wywołujący wywołujący narzędzia diagnostyczne](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w polu **Bieżąca funkcja** `GetNumber` (, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest wyświetlana po lewej stronie w obszarze **Funkcja** wywołująca , a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **Wywołano** funkcje po prawej stronie. (Możesz wybrać oba pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i procent całkowitego czasu działania aplikacji, który zajęło ukończenie funkcji.

    **Treść funkcji** pokazuje również łączną ilość czasu (i procent czasu) spędzonego w treści funkcji z wyłączeniem czasu spędzonego na wywołaniach i wywołanych funkcjach. (Na tej ilustracji 2856 z 2863 ms zostało spędzonych w treści funkcji, a pozostały czas (<20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję. Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Wysokie wartości w treści **funkcji mogą** wskazywać wąskie gardło wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci w](../profiling/memory-usage.md)celu zidentyfikowania wąskich gardeł wydajności.
- [Przeanalizuj](../profiling/cpu-usage.md) użycie procesora CPU, aby uzyskać bardziej szczegółowe informacje na temat narzędzia użycia procesora CPU.
- Przeanalizuj użycie procesora CPU bez dołączonego debugera [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) lub przez skierowanie go do uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz Zbieranie danych profilowania bez debugowania w tece Uruchamianie narzędzi profilowania z [debugerem](../profiling/running-profiling-tools-with-or-without-the-debugger.md)lub bez niego.

## <a name="see-also"></a>Zobacz też

- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
