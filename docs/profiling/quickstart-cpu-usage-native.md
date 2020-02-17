---
title: Analizowanie danych użycia procesora CPUC++()
description: Mierzenie wydajności aplikacji w C++ programie przy użyciu narzędzia diagnostyki użycia procesora CPU
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
ms.openlocfilehash: 5912e433f4d2bc05dc4e460456c8858af82183f6
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279218"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Szybki Start: analizowanie danych użycia procesora CPU w programieC++Visual Studio ()

Program Visual Studio udostępnia wiele zaawansowanych funkcji, które ułatwiają analizowanie problemów z wydajnością w aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji. W tym miejscu znajdziesz narzędzie do identyfikowania wąskich gardeł wydajności z powodu wysokiego użycia procesora CPU. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli opisane w tym miejscu narzędzie **użycie procesora CPU** nie poda potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji rejestracji i analizowaniu tego rodzaju danych.

System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ). W systemie Windows 7 i nowszych można użyć narzędzia do wykonywania w programie do [profilowania](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio i Utwórz projekt.

   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

   W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Wizualizacja C++** , a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**. Następnie nadaj nazwę projektowi *Diagnostics_Get_Started_Native*.

   Jeśli szablon projektu **aplikacji konsolowej systemu Windows** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . Uruchamia Instalatora programu Visual Studio. Wybierz pozycję **programowanie C++ dla komputerów stacjonarnych** , a następnie wybierz polecenie **Modyfikuj**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **C++** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli szablon **aplikacji konsolowej** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Następnie w Instalator programu Visual Studio wybierz pozycję **Programowanie dla komputerów z C++**  obciążeniem.

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

    z tym kodem (nie należy usuwać `#include "stdafx.h"`):

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

## <a name="step-1-collect-profiling-data"></a>Krok 1: Zbierania danych profilowania

1. Najpierw ustaw punkt przerwania w aplikacji w tym wierszu kodu w funkcji `main`:

    `for (int i = 0; i < 10; ++i) {`

    Ustaw punkt przerwania, klikając na marginesie na lewo od wiersza kodu.

2. Następnie ustaw drugi punkt przerwania na zamykającym nawiasie klamrowym na końcu funkcji `main`:

     ![Ustawianie punktów przerwania na potrzeby profilowania](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Ustawianie punktów przerwania na potrzeby profilowania")

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.

3. Okno **Narzędzia diagnostyczne** jest już widoczne, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **debuguj** > **Windows** > **Pokaż narzędzia diagnostyczne**.

4. Kliknij pozycję **debuguj** > **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok **Podsumowanie** narzędzi diagnostycznych.

5. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU przez wybranie opcji **Rejestruj profil procesora**, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/quickstart-cpu-usage-summary.png "Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU")

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

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji kliknij dwukrotnie funkcję `getNumber`.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywoływany przez obiekt wywołujący narzędzi diagnostycznych](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** (`getNumber`w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w obszarze **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.

    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (Na tym rysunku 119 z 43602 MS były spędzane w treści funkcji, a pozostały czas spędzony w innym kodzie wywoływanym przez tę funkcję). Rzeczywiste wartości będą się różnić w zależności od środowiska.

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

## <a name="next-steps"></a>Następne kroki

- [Analizuj użycie pamięci](../profiling/memory-usage.md), aby zidentyfikować wąskie gardła wydajności.
- [Analizuj użycie procesora](../profiling/cpu-usage.md) , aby uzyskać bardziej szczegółowe informacje o narzędziu Użycie procesora CPU.
- Analizuj użycie procesora bez dołączonego debugera lub jako przeznaczonego dla uruchomionej aplikacji — aby uzyskać więcej informacji, zobacz [zbieranie danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [narzędziach profilowania uruchamiania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
