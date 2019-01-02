---
title: Analizowanie danych użycia procesora CPU (C++)
description: Mierzyć wydajność aplikacji w języku C++ za pomocą narzędzia do diagnostyki użycia procesora CPU
ms.date: 08/06/2018
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 38bacd51727ea2091e23adb606ff65de901f479a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883175"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Szybki start: Analizowanie danych użycia procesora CPU w Visual Studio (C++)

Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w analizie problemów z wydajnością w aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji. W tym miejscu przyjrzymy się narzędzie, aby określić wąskie gardła wydajności ze względu na wysokie użycie procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** narzędzia opisane w tym miejscu nie umożliwiają danych, których potrzebują, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji rejestracji i analizowaniu tego rodzaju danych.

Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno). Windows 7 lub nowszy, można użyć narzędzia do późniejszej analizy [Profiler wydajności](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

2. W obszarze **Visual C++**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **aplikacji konsoli Windows**.

    Jeśli nie widzisz **aplikacji konsoli Windows** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **Diagnostics_Get_Started_Native** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W *MyDbgApp.cpp*, Zastąp następujący kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    przy użyciu tego kodu (nie należy usuwać `#include "stdafx.h"`):

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
  
1.  Najpierw ustaw punkt przerwania w swojej aplikacji, w tym wierszu kodu w `main` funkcji:

    `for (int i = 0; i < 10; ++i) {`

    Ustaw punkt przerwania, klikając na marginesie po lewej stronie wiersza kodu.

2.  Następnym etapem jest skonfigurowanie drugiego punktu przerwania na zamykającego nawiasu klamrowego na końcu `main` funkcji:

     ![Ustaw punkty przerwania dla profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "ustawiać punkty przerwania dla profilowania")

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.
  
3.  **Narzędzia diagnostyczne** okna jest jeszcze widoczny, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

4.  Kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Gdy aplikacja zakończy ładowanie, **Podsumowanie** zostanie wyświetlony widok narzędzia diagnostyczne.

5.  Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU, wybierając **profil procesora CPU rekordu**, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyczne Włącz profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "narzędzia diagnostyczne Włącz profilowanie procesora CPU")

     Po włączeniu funkcji zbierania danych, przycisk Nagraj wyświetla czerwone kółko.

     Po wybraniu **profil procesora CPU rekordu**, Visual Studio spowoduje rozpoczęcie rejestrowania funkcji i czas, jaki przyjmują do wykonania, a także zawiera wykres osi czasu, można użyć, aby skoncentrować się na poszczególnych segmentach sesji pobierania próbek. Ta zebrane dane może wyświetlać tylko w przypadku, gdy aplikacja jest zatrzymywane w punkcie przerwania.

6.  Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.
  
     Narzędzie użycie procesora CPU wyświetla raport w **użycie procesora CPU** kartę.

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji dwukrotnie kliknij `getNumber` funkcji.

    Po dwukrotnym kliknięciu funkcji **wywołujący/wywoływany** w okienku po lewej stronie zostanie otwarty widok. 

    ![Widok wywoływany obiekt wywołujący narzędzia do diagnostyki](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji pojawia się w nagłówku i w **bieżącą funkcję** pole (`getNumber`, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, oraz wszelkie funkcje wywołane przez bieżącą funkcję są pokazane w **funkcji o nazwie** pole po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Funkcja treści** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. (Na tej ilustracji ms 119 poza 43602 spędzono w treści funkcji, a w innym kodzie wywoływanych przez tę funkcję tracony jest czas pozostały). Rzeczywiste wartości będzie się bardzo różnić w zależności od środowiska.

    > [!TIP]
    > O wysokiej wartości w **treści funkcji** może wskazać wąskie gardło w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizowanie użycia pamięci](../profiling/memory-usage.md)do identyfikowania wąskich gardeł wydajności.
- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md) uzyskać bardziej szczegółowe informacje na temat narzędzia użycie procesora CPU.
- Analizowanie użycia procesora CPU bez debugera dołączone lub stosując uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz także  

 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
