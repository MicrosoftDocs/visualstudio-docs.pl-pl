---
title: Mierzenie użycia procesora CPU w aplikacjach
description: Analizuj problemy z wydajnością procesora CPU w aplikacji za pomocą narzędzi diagnostycznych zintegrowanych z debugerem.
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3a7c5eb8aa489da9ced0803e0f83855734825ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537374"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Mierzenie wydajności aplikacji przez analizowanie użycia procesora CPU

Za pomocą narzędzi profilowania programu Visual Studio można analizować problemy z wydajnością w aplikacji. W tym artykule przedstawiono sposób korzystania z karty **użycie procesora CPU** narzędzi diagnostycznych w celu uzyskania danych wydajności dla aplikacji.

Po wstrzymaniu debugera narzędzie **użycie procesora CPU** zbiera informacje o funkcjach, które są wykonywane w aplikacji. Narzędzie wyświetla listę funkcji, które zostały wykonane i zawiera wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania.

Centrum diagnostyki oferuje wiele innych opcji umożliwiających uruchomienie sesji diagnostycznej i zarządzanie nią. Jeśli **użycie procesora CPU** nie zapewnia potrzebnych danych, [inne narzędzia profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. W wielu przypadkach wąskie gardła wydajności aplikacji może być spowodowane przez coś innego niż procesor CPU, takich jak pamięć, interfejs użytkownika renderowania lub czas żądania sieci. Centrum diagnostyki oferuje wiele innych opcji rejestrowania i analizowania tego rodzaju danych.

> [!Important]
> Narzędzia diagnostyczne obsługują Programowanie dla platformy .NET w programie Visual Studio, w tym ASP.NET, oraz na potrzeby programowania natywnego/C++.

W tym artykule omówiono Analizowanie użycia procesora CPU w normalnym przepływie debugowania. Możesz również analizować użycie procesora bez dołączania debugera lub jako docelowej działającej aplikacji. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Możesz również użyć innego narzędzia profilowania, [Funkcja PerfTip](../profiling/perftips.md), aby przejść przez kod i określić, jak długo trwa wykonywanie określonych funkcji lub bloków kodu.

Narzędzi profilowania można używać bez debugera z systemem Windows 7 i nowszymi wersjami. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ).

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Zbieranie danych użycia procesora CPU
> * Analizowanie danych użycia procesora CPU

## <a name="step-1-collect-profiling-data"></a>Krok 1. zbieranie danych profilowania

1. Otwórz projekt, który ma być debugowany w programie Visual Studio, i ustaw punkt przerwania w aplikacji w punkcie, w którym chcesz przeanalizować użycie procesora.

2. Ustaw drugi punkt przerwania na końcu funkcji lub regionu kodu, który chcesz analizować.

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które mają być analizowane.

3. Okno **Narzędzia diagnostyczne** jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Można wybrać, czy ma być wyświetlane **użycie procesora CPU**, [użycie pamięci](../profiling/Memory-Usage.md), czy oba, z ustawieniem **Wybierz Narzędzia** na pasku narzędzi. Jeśli używasz Visual Studio Enterprise, możesz również włączyć lub wyłączyć IntelliTrace w opcji **Narzędzia**  >  **Options**  >  **IntelliTrace**.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Będziemy głównie sprawdzać użycie procesora CPU, dlatego należy upewnić się, że **użycie procesora CPU** jest włączone (domyślnie włączone).

5. Kliknij pozycję **Debuguj**  >  **Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok Podsumowanie narzędzi diagnostycznych. Jeśli musisz otworzyć okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Wyszukiwanie i filtrowanie zdarzeń na karcie zdarzenia okna narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania zostanie osiągnięty.

7. Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU, a następnie otwórz kartę **użycie procesora CPU** .

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora CPU](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Po wybraniu opcji **Rejestruj profil procesora CPU**program Visual Studio rozpocznie nagrywanie funkcji i czas ich wykonania. Te zebrane dane można wyświetlić tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

8. Naciśnij klawisz F5, aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane wydajności dla aplikacji przeznaczone dla regionu kodu, który jest uruchamiany między dwoma punktami przerwania.

     Profiler rozpoczyna Przygotowywanie danych wątku. Poczekaj na zakończenie.

     ![Narzędzia diagnostyczne przygotowujące wątki](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     Narzędzie użycie procesora CPU wyświetla raport na karcie **użycie procesora CPU** .

     ![Karta użycie procesora CPU narzędzi diagnostycznych](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Jeśli chcesz wybrać bardziej konkretny region kodu do analizy, wybierz region na osi czasu procesora (musi to być region, w którym są wyświetlane dane profilowania).

     ![Narzędzia diagnostyczne wybierające segment czasu](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     W tym momencie można rozpocząć analizowanie danych.

     > [!TIP]
     >  Podczas próby zidentyfikowania problemów z wydajnością wykonaj wiele pomiarów. Wydajność w sposób naturalny różni się od uruchomienia do uruchomienia, a ścieżki kodu są zwykle wykonywane wolniej podczas pierwszego uruchomienia z powodu jednokrotnej inicjacji, takiej jak ładowanie bibliotek DLL, metody kompilacji JIT i Inicjowanie pamięci podręcznych. Pobierając wiele pomiarów, można lepiej poznać zakres i medianę pokazywanej metryki, co pozwala na porównanie pierwszego stanu w porównaniu z stabilnym działaniem w obszarze kodu.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. analizowanie danych użycia procesora CPU

Zalecamy rozpoczęcie analizowania danych przez badanie listy funkcji w obszarze użycie procesora CPU, zidentyfikowanie funkcji, które są najbardziej potrzebne, a następnie przeprowadzenie bliższej kontroli nad każdą z nich.

1. Na liście funkcji zapoznaj się z funkcjami, które działają najlepiej.

    ![Lista funkcji użycia procesora CPU narzędzi diagnostycznych](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Funkcje są wymienione w kolejności rozpoczynającej się od tych, w których są wykonywane najwięcej pracy (nie są w kolejności wywołań). Dzięki temu możesz szybko identyfikować najdłuższe uruchomione funkcje.

2. Na liście funkcji kliknij dwukrotnie jedną z funkcji aplikacji, która wykonuje wiele pracy.

    Po dwukrotnym kliknięciu funkcji, w okienku po lewej stronie zostanie otwarty widok **wywołujący/wywoływany** .

    ![Widok wywoływany przez obiekt wywołujący narzędzi diagnostycznych](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w **bieżącym oknie funkcji** (GetNumber, w tym przykładzie). Funkcja, która wywołała bieżącą funkcję, jest pokazywana po lewej stronie w sekcji **wywoływanie funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **wywoływane funkcje** po prawej stronie. (Możesz wybrać jedno z pól, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (MS) i procent całkowitego czasu działania aplikacji, który wykonał działanie.
    **Treść funkcji** pokazuje również łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. (W tym przykładzie 2367 z 2389 MS zostało zużyte w treści funkcji, a pozostałe 22 MS nastąpiło w kodzie zewnętrznym wywoływanym przez tę funkcję).

    > [!TIP]
    > Duże wartości w **treści funkcji** mogą wskazywać wąskie gardła wydajności w samej funkcji.

3. Aby wyświetlić widok wyższego poziomu z kolejnością, w której są wywoływane funkcje, wybierz opcję **drzewo wywołań** z listy rozwijanej w górnej części okienka.

    Każdy numerowany obszar na rysunku odnosi się do kroku procedury.

    ::: moniker range=">=vs-2019"
    ![Drzewo wywołań narzędzi diagnostycznych](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Drzewo wywołań narzędzi diagnostycznych](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Obraz|Opis|
    |-|-|
    |![Krok 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołań użycia procesora CPU jest pseudo-węzłem|
    |![Krok 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|W większości aplikacji, gdy opcja [Pokaż zewnętrzny kod](#view-external-code) jest wyłączona, węzeł drugiego poziomu jest węzłem **[zewnętrzny kod]** zawierającym kod systemowy i program, który rozpoczyna i kończy działanie aplikacji, rysuje interfejs użytkownika, kontroluje planowanie wątków i udostępnia inne usługi niskiego poziomu aplikacji.|
    |![Krok 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu to metody kodu użytkownika i procedury asynchroniczne, które są wywoływane lub tworzone przez system i kod struktury drugiego poziomu.|
    |![Krok 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko dla wywołań metody nadrzędnej. Gdy **Pokaż zewnętrzny kod** jest wyłączony, metody aplikacji mogą również zawierać węzeł **[kod zewnętrzny]** .|

    Poniżej znajduje się więcej informacji na temat wartości kolumn:

    - **Łączny czas CPU** wskazuje, ile pracy zostało wykonane przez funkcję i wszystkie funkcje wywołane przez nią. Wysoka całkowita wartość procesora CPU wskazuje funkcje, które są najbardziej kosztowne.

    - **Własny procesor CPU** wskazuje, ile pracy zostało wykonane przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały przez nią wywołane. Wysokie wartości **procesora CPU** mogą wskazywać wąskie gardła wydajności w samej funkcji.

    - **Moduły** Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].

    ::: moniker range=">=vs-2019"
    Aby wyświetlić wywołania funkcji, które używają najwyższej wartości procentowej przepustowości procesora w widoku drzewa wywołań, kliknij przycisk **Rozwiń ścieżkę gorącą**.

    ![Gorąca ścieżka narzędzi diagnostycznych](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Jeśli zobaczysz kod w drzewie wywołań oznaczony jako "uszkodzony" lub "stos niemożliwy do przewidzenia", oznacza to, że zdarzenia śledzenia zdarzeń systemu Windows (ETW) zostały największej. Spróbuj zebrać ten sam ślad przy drugim czasie, aby rozwiązać ten problem.

## <a name="view-external-code"></a>Wyświetl kod zewnętrzny

Kod zewnętrzny to funkcje składników system i Framework, które są wykonywane przez zapisanie kodu. Kod zewnętrzny obejmuje funkcje, które uruchamiają i zatrzymują aplikację, rysują interfejs użytkownika, sterują wątkami i dostarczają do aplikacji inne usługi niskiego poziomu. W większości przypadków nie jest interesujący kod zewnętrzny, dlatego narzędzie użycie procesora CPU zbiera funkcje zewnętrzne metody użytkownika w jednym węźle **[kod zewnętrzny]** .

Aby wyświetlić ścieżki wywołań kodu zewnętrznego, wybierz pozycję **Pokaż kod zewnętrzny** z listy **widok filtru** , a następnie wybierz pozycję **Zastosuj**.

![Wybierz widok filtru, a następnie Pokaż kod zewnętrzny](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Należy pamiętać, że wiele łańcuchów połączeń kodu zewnętrznego jest głęboko zagnieżdżonych, dzięki czemu szerokość kolumny nazwy funkcji może przekroczyć szerokość wyświetlania wszystkich, ale większość monitorów komputerów. W takim przypadku nazwy funkcji są wyświetlane jako **[...]**.

Użyj pola wyszukiwania, aby znaleźć węzeł, którego szukasz, a następnie użyj poziomego paska przewijania, aby przenieść dane do widoku.

> [!TIP]
> Jeśli profiluje się zewnętrzny kod, który wywołuje funkcje systemu Windows, należy upewnić się, że masz najnowszą. pliki *PDB* . Bez tych plików widoki raportów wyświetlają nazwy funkcji systemu Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji o tym, jak upewnić się, że masz potrzebne pliki, zobacz [Określanie symboli (. pdb) i plików źródłowych w debugerze](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku pokazano, jak zbierać i analizować dane użycia procesora CPU. Jeśli zostały już wykonane [pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md), warto zapoznać się z tematem jak analizować użycie pamięci w aplikacjach.

> [!div class="nextstepaction"]
> [Użycie pamięci profilu w programie Visual Studio](../profiling/memory-usage.md)
