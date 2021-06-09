---
title: Analizowanie danych użycia procesora CPU (C++)
description: Mierzenie wydajności aplikacji w języku C++ przy użyciu narzędzia diagnostycznego Użycie procesora CPU
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8c68cc67d768dbe2b1c42671a02360e5cef2b56b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760942"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Szybki start: analizowanie danych użycia procesora CPU w Visual Studio (C++)

Aplikacja Visual Studio wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób na nauczenia się niektórych podstawowych funkcji. W tym miejscu przyjrzymy się narzędziu, aby zidentyfikować wąskie gardła wydajności spowodowane wysokim użyciem procesora CPU. Narzędzia diagnostyczne są obsługiwane na potrzeby programowania na platformie .NET w Visual Studio, w tym ASP.NET, a także w przypadku programowania natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji uruchamiania sesji diagnostyki i zarządzania nimi. Jeśli narzędzie **Użycie procesora CPU** opisane w tym miejscu nie dostarcza potrzebnych danych, inne narzędzia [profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być przydatne. W wielu przypadkach wąskie gardło wydajności aplikacji może być spowodowane przez coś innego niż procesor, taki jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. Ten profiler wydajności oferuje wiele innych opcji do nagrywania i analizowania tego rodzaju danych. [PerfTips](../profiling/perftips.md), inne narzędzie profilowania zintegrowane z debugerem, umożliwia również krok po kroku kod i określenie, jak długo trwa ukończenie określonych funkcji lub bloków kodu.

Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (**narzędzia diagnostyczne** okno). W systemie Windows 7 lub nowszym można użyć narzędzia post mortem, profiler wydajności [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz Visual Studio i utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **File** New Project > **(Nowy projekt** > **pliku).**

   W **oknie dialogowym Nowy** projekt w okienku po lewej stronie **rozwiń** pozycję Visual C++ , a następnie wybierz pozycję **Windows Desktop.** W środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows.** Następnie nadaj *projektowi nazwę Diagnostics_Get_Started_Native*.

   Jeśli nie widzisz szablonu projektu Aplikacja konsolowa systemu **Windows,** wybierz link **Otwórz** Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji klasycznych w języku C++,** a następnie wybierz pozycję **Modyfikuj.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję **Okno** > **uruchamiania pliku**.

   W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   W **oknie Create a new project (Tworzenie** nowego projektu) wprowadź lub wpisz *console* (konsola) w polu wyszukiwania. Następnie wybierz pozycję **C++** z listy Język, a następnie wybierz **pozycję Windows** z listy Platforma.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa,** a następnie wybierz pozycję **Dalej.**

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli,** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji. Następnie w Instalator programu Visual Studio wybierz obciążenie **Tworzenie aplikacji klasycznych w języku C++.**

   W **oknie Konfigurowanie nowego projektu** wpisz lub Diagnostics_Get_Started_Native *w* **polu Nazwa** projektu. Następnie wybierz pozycję **Utwórz.**

   ::: moniker-end

   Visual Studio otworzy nowy projekt.

1. W *Diagnostics_Get_Started_Native* zastąp następujący kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    za pomocą tego kodu (nie usuwaj `#include "stdafx.h"` ):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>

    //.cpp file code:

    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;

    int getNumber()
    {

        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();

        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here
        // to increase CPU usage
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }

    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;

        auto x = getNumber();
    }

    int main()
    {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `main` funkcji :

    `for (int i = 0; i < 10; ++i) {`

    Ustaw punkt przerwania, klikając utter z lewej strony wiersza kodu.

2. Następnie ustaw drugi punkt przerwania w zamykającym nawiasie klamrowy na końcu `main` funkcji:

     ![Ustawianie punktów przerwania na czas profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Ustawianie punktów przerwania na czas profilowania")

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które chcesz analizować.

3. Okno **narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję  >  **Debuguj okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Kliknij **pozycję**  >  **Debuguj rozpocznij debugowanie** (lub **Uruchom** na pasku narzędzi lub naciśnij **klawisz F5).**

     Po zakończeniu ładowania aplikacji zostanie **wyświetlony widok** Podsumowanie narzędzi diagnostycznych.

5. Gdy debuger jest wstrzymany, włącz zbieranie danych użycia procesora CPU, wybierając pozycję Rejestruj profil **procesora CPU,** a następnie otwórz **kartę Użycie procesora** CPU.

     ![Narzędzia diagnostyczne włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "Narzędzia diagnostyczne włącz profilowanie procesora CPU")

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

     ![Karta Użycie procesora CPU w narzędziach diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "Karta DiagToolsCPUUsage")

    > [!TIP]
    > Funkcje są wyświetlane w kolejności rozpoczynającej się od tych, które pracują najlepiej (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłużej działające funkcje.

2. Na liście funkcji kliknij dwukrotnie `getNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji widok **wywołujący/wywołujący/wywołujący** zostanie otwarty w okienku po lewej stronie.

    ![Widok wywołujący wywołujący narzędzia diagnostyczne](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w polu **Bieżąca funkcja** `getNumber` (, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest wyświetlana po lewej stronie w obszarze **Funkcja** wywołująca , a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **Wywołano** funkcje po prawej stronie. (Możesz wybrać oba pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i procent całkowitego czasu działania aplikacji, który zajęło ukończenie funkcji.

    **Treść funkcji** pokazuje również łączną ilość czasu (i procent czasu) spędzonego w treści funkcji z wyłączeniem czasu spędzonego na wywołaniach i wywołanych funkcjach. (Na tej ilustracji 119 z 43602 ms zostało spędzonych w treści funkcji, a pozostały czas został spędzony w innym kodzie wywoływanym przez tę funkcję). Rzeczywiste wartości będą bardzo różne w zależności od środowiska.

    > [!TIP]
    > Wysokie wartości w treści **funkcji mogą** wskazywać wąskie gardło wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci w](../profiling/memory-usage.md)celu zidentyfikowania wąskich gardeł wydajności.
- [Przeanalizuj](../profiling/cpu-usage.md) użycie procesora CPU, aby uzyskać bardziej szczegółowe informacje na temat narzędzia użycia procesora CPU.
- Przeanalizuj użycie procesora CPU bez dołączonego debugera [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) lub przez skierowanie go do uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz Zbieranie danych profilowania bez debugowania w tece Uruchamianie narzędzi profilowania z [debugerem](../profiling/running-profiling-tools-with-or-without-the-debugger.md)lub bez niego.

## <a name="see-also"></a>Zobacz też

- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
