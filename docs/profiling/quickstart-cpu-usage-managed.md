---
title: Analizowanie danych użycia procesora CPU (kod zarządzany)
description: Mierzyć wydajność aplikacji w języku C# i Visual Basic, za pomocą narzędzia do diagnostyki użycia procesora CPU
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
- dotnet
ms.openlocfilehash: 05dbbf5bc6e13b36e5918a880d0a767968a78f30
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703859"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-managed-code"></a>Szybki start: Analizowanie danych użycia procesora CPU w programie Visual Studio (kod zarządzany)

Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w analizie problemów z wydajnością w aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji. W tym miejscu przyjrzymy się narzędzie, aby określić wąskie gardła wydajności ze względu na wysokie użycie procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisane w tym miejscu nie umożliwiają danych, których potrzebują, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji rejestracji i analizowaniu tego rodzaju danych.

Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno). Windows 7 lub nowszy, można użyć narzędzia do późniejszej analizy [Profiler wydajności](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

2. W obszarze **Visual C#** lub **języka Visual Basic**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET Framework)**.

    Jeśli nie widzisz **aplikacja Konsolowa** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych .NET** obciążenia, wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **MyProfilerApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

2. Otwórz *Program.cs* i Zastąp cały kod następującym kodem:

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
    > W języku Visual Basic, upewnij się, obiekt startowy jest ustawiony na `Sub Main` (**właściwości** > **aplikacji** > **obiekt początkowy**).

## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w swojej aplikacji, w tym wierszu kodu w `Main` funkcji:

    `for (int i = 0; i < 200; i++)`

    lub, w przypadku języka Visual Basic:

    `For i As Integer = 0 To 199`

    Ustaw punkt przerwania, klikając na marginesie po lewej stronie wiersza kodu.

2. Następnym etapem jest skonfigurowanie drugiego punktu przerwania na zamykającego nawiasu klamrowego na końcu `Main` funkcji:

     ![Ustaw punkty przerwania dla profilowania](../profiling/media/quickstart-cpu-usage-breakpoints.png "ustawiać punkty przerwania dla profilowania")

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.

3. **Narzędzia diagnostyczne** okna jest jeszcze widoczny, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

4. Kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Gdy aplikacja zakończy ładowanie, **Podsumowanie** zostanie wyświetlony widok narzędzia diagnostyczne.

5. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU, wybierając **profil procesora CPU rekordu**, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyczne Włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "narzędzia diagnostyczne Włącz profilowanie procesora CPU")

     Po włączeniu funkcji zbierania danych, przycisk Nagraj wyświetla czerwone kółko.

     Po wybraniu **profil procesora CPU rekordu**, Visual Studio spowoduje rozpoczęcie rejestrowania funkcji i czas, jaki przyjmują do wykonania, a także zawiera wykres osi czasu, można użyć, aby skoncentrować się na poszczególnych segmentach sesji pobierania próbek. Ta zebrane dane może wyświetlać tylko w przypadku, gdy aplikacja jest zatrzymywane w punkcie przerwania.

6. Naciśnij klawisz **F5** do uruchomienia aplikacji na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.

     Narzędzie użycie procesora CPU wyświetla raport w **użycie procesora CPU** kartę.

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji dwukrotnie kliknij `ServerClass::GetNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** w okienku po lewej stronie zostanie otwarty widok.

    ![Widok wywoływany obiekt wywołujący narzędzia do diagnostyki](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji pojawia się w nagłówku i w **bieżącą funkcję** pole (`GetNumber`, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, oraz wszelkie funkcje wywołane przez bieżącą funkcję są pokazane w **funkcji o nazwie** pole po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Funkcja treści** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. (Na tej ilustracji 2856 poza 2863 ms spędzono w treści funkcji i pozostały czas (< 20 ms) był poświęcony w kodzie zewnętrznych wywoływanych przez tę funkcję). Rzeczywiste wartości może się różnić w zależności od środowiska.

    > [!TIP]
    > O wysokiej wartości w **treści funkcji** może wskazać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do identyfikowania wąskich gardeł wydajności.
- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md) uzyskać bardziej szczegółowe informacje na temat narzędzia użycie procesora CPU.
- Analizowanie użycia procesora CPU bez debugera dołączone lub stosując uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
