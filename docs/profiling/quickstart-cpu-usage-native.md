---
title: Analizowanie danych użycia procesora CPU (C++)
description: Mierzenie wydajności aplikacji w języku C++ przy użyciu narzędzia do diagnostyki użycia procesora CPU
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6e721a424cc1c8b7202764fdc9b23eae737d22a4
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90074881"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Szybki Start: analizowanie danych użycia procesora CPU w programie Visual Studio (C++)

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. W tym miejscu znajdziesz narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne obsługują Programowanie dla platformy .NET w programie Visual Studio, w tym ASP.NET, oraz na potrzeby programowania natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji umożliwiających uruchomienie sesji diagnostycznej i zarządzanie nią. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskie gardła wydajności aplikacji może być spowodowane przez coś innego niż procesor CPU, takich jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. Profiler wydajności oferuje wiele innych opcji rejestrowania i analizowania tego rodzaju danych. [Funkcja PerfTip](../profiling/perftips.md), inne narzędzie profilowania zintegrowanego debugera, umożliwia również przechodzenie przez kod i określenie, jak długo trwa wykonywanie określonych funkcji lub bloków kodu.

System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i Utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

   W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual C++**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**. Następnie nadaj nazwę projektowi *Diagnostics_Get_Started_Native*.

   Jeśli szablon projektu **aplikacji konsolowej systemu Windows** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Zostanie uruchomiona Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik** > **startowy**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C++** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli szablon **aplikacji konsolowej** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz pozycję **Programowanie aplikacji klasycznych w języku C++** .

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *Diagnostics_Get_Started_Native* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ::: moniker-end

   Program Visual Studio otwiera nowy projekt.

1. W *Diagnostics_Get_Started_Native*Zastąp następujący kod

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

## <a name="step-1-collect-profiling-data"></a>Krok 1. zbieranie danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w `main` funkcji:

    `for (int i = 0; i < 10; ++i) {`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

2. Następnie ustaw drugi punkt przerwania dla zamykającego nawiasu klamrowego na końcu `main` funkcji:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Ustawianie punktów przerwania na potrzeby profilowania")

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które mają być analizowane.

3. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Kliknij pozycję **Debuguj**  >  **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok **Podsumowanie** narzędzi diagnostycznych.

5. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU przez wybranie opcji **Rejestruj profil procesora**, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU")

     Gdy zbieranie danych jest włączone, przycisk Rejestruj wyświetla czerwony okrąg.

     Po wybraniu opcji **Rejestruj profil procesora CPU**program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonywania, a także wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

6. Naciśnij klawisz F5, aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane wydajności dla aplikacji przeznaczone dla regionu kodu, który jest uruchamiany między dwoma punktami przerwania.

     Profiler rozpoczyna Przygotowywanie danych wątku. Poczekaj na zakończenie.

     Narzędzie użycie procesora CPU wyświetla raport na karcie **użycie procesora CPU** .

     W tym momencie można rozpocząć analizowanie danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych przez badanie listy funkcji w obszarze użycie procesora CPU, zidentyfikowanie funkcji, które są najbardziej potrzebne, a następnie przeprowadzenie bliższej kontroli nad każdą z nich.

1. Na liście funkcji zapoznaj się z funkcjami, które działają najlepiej.

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności rozpoczynającej się od tych, w których są wykonywane najwięcej pracy (nie są w kolejności wywołań). Dzięki temu możesz szybko identyfikować najdłuższe uruchomione funkcje.

2. Na liście funkcji kliknij dwukrotnie `getNumber` funkcję.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywoływany przez obiekt wywołujący narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** ( `getNumber` w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w obszarze **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (MS) i procent całkowitego czasu działania aplikacji, który wykonał działanie.

    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (Na tym rysunku 119 z 43602 MS były spędzane w treści funkcji, a pozostały czas spędzony w innym kodzie wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizuj użycie pamięci](../profiling/memory-usage.md), aby zidentyfikować wąskie gardła wydajności.
- [Analizuj użycie procesora](../profiling/cpu-usage.md) , aby uzyskać bardziej szczegółowe informacje o narzędziu Użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
