---
title: Analizowanie danych użycia procesora CPU (C#, Visual Basic)
description: Mierzenie wydajności aplikacji w języku C# i Visual Basic przy użyciu narzędzia do diagnostyki użycia procesora CPU
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
- dotnet
ms.openlocfilehash: 663a9c9e5e76792b4478d6ecca3043a8a2893268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80412001"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Szybki Start: analizowanie danych użycia procesora CPU w programie Visual Studio (C#, Visual Basic)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. W tym miejscu znajdziesz narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne obsługują Programowanie dla platformy .NET w programie Visual Studio, w tym ASP.NET, oraz na potrzeby programowania natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji umożliwiających uruchomienie sesji diagnostycznej i zarządzanie nią. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskie gardła wydajności aplikacji może być spowodowane przez coś innego niż procesor CPU, takich jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. Centrum diagnostyki oferuje wiele innych opcji rejestrowania i analizowania tego rodzaju danych. [Funkcja PerfTip](../profiling/perftips.md), inne narzędzie profilowania zintegrowanego debugera, umożliwia również przechodzenie przez kod i określenie, jak długo trwa wykonywanie określonych funkcji lub bloków kodu.

System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i Utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

   W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **C#** lub **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nadaj nazwę projektowi *MyProfilerApp*.

   Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik** > **startowy**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyProfilerApp* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ::: moniker-end

   Program Visual Studio otwiera nowy projekt.

2. Otwórz *program.cs* i Zastąp cały kod następującym kodem:

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
    > W Visual Basic upewnij się, że obiekt uruchamiania jest ustawiony na `Sub Main` (**Właściwości**  >  **Application**  >  **obiekt uruchamiania**aplikacji).

## <a name="step-1-collect-profiling-data"></a>Krok 1. zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `Main` funkcji:

    `for (int i = 0; i < 200; i++)`

    lub, w przypadku Visual Basic:

    `For i As Integer = 0 To 199`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

2. Następnie ustaw drugi punkt przerwania dla zamykającego nawiasu klamrowego na końcu `Main` funkcji:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints.png "Ustawianie punktów przerwania na potrzeby profilowania")

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które mają być analizowane.

3. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Kliknij pozycję **Debuguj**  >  **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok **Podsumowanie** narzędzi diagnostycznych.

5. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU przez wybranie opcji **Rejestruj profil procesora**, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU")

     Gdy zbieranie danych jest włączone, przycisk Rejestruj wyświetla czerwony okrąg.

     Po wybraniu opcji **Rejestruj profil procesora CPU**program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonywania, a także wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz **F5** , aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane wydajności dla aplikacji przeznaczone dla regionu kodu, który jest uruchamiany między dwoma punktami przerwania.

     Profiler rozpoczyna Przygotowywanie danych wątku. Poczekaj na zakończenie.

     Narzędzie użycie procesora CPU wyświetla raport na karcie **użycie procesora CPU** .

     W tym momencie można rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych przez badanie listy funkcji w obszarze użycie procesora CPU, zidentyfikowanie funkcji, które są najbardziej potrzebne, a następnie przeprowadzenie bliższej kontroli nad każdą z nich.

1. Na liście funkcji zapoznaj się z funkcjami, które działają najlepiej.

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności rozpoczynającej się od tych, w których są wykonywane najwięcej pracy (nie są w kolejności wywołań). Dzięki temu możesz szybko identyfikować najdłuższe uruchomione funkcje.

2. Na liście funkcji kliknij dwukrotnie `ServerClass::GetNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywoływany przez obiekt wywołujący narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** ( `GetNumber` w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w obszarze **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (MS) i procent całkowitego czasu działania aplikacji, który wykonał działanie.

    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (Na tym rysunku 2856 z 2863 MS były spędzane w treści funkcji, a pozostały czas (<20 ms) został spędzony w kodzie zewnętrznym wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizuj użycie pamięci](../profiling/memory-usage.md), aby zidentyfikować wąskie gardła wydajności.
- [Analizuj użycie procesora](../profiling/cpu-usage.md) , aby uzyskać bardziej szczegółowe informacje o narzędziu Użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
