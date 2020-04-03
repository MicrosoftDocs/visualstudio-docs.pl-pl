---
title: Mierzenie użycia procesora w aplikacjach
description: Analizowanie problemów z wydajnością procesora w aplikacji przy użyciu narzędzi diagnostycznych zintegrowanych z debugerem.
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
ms.openlocfilehash: 5134e17c26ffd7b34c0277c571173ba03d758bee
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638784"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Mierz wydajność aplikacji, analizując użycie procesora

Narzędzia do profilowania programu Visual Studio umożliwiają analizowanie problemów z wydajnością w aplikacji. W tym artykule pokazano, jak używać karty **Użycie procesora CPU** w narzędziach diagnostycznych w celu uzyskania danych o wydajności aplikacji.

Po wstrzymaniu debugera narzędzie **Użycie procesora CPU** zbiera informacje o funkcjach wykonywanych w aplikacji. Narzędzie wyświetla listę funkcji, które wykonywały pracę i udostępnia wykres osi czasu, którego można użyć do skupienia się na określonych segmentach sesji próbkowania.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesją diagnostyczną. Jeśli **użycie procesora CPU** nie daje danych, które są potrzebne, inne narzędzia [profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla Ciebie. W wielu przypadkach wąskie gardło wydajności aplikacji może być spowodowane przez coś innego niż procesor, takich jak pamięć, renderowanie interfejsu użytkownika lub czas żądania sieci. Centrum diagnostyki oferuje wiele innych opcji do rejestrowania i analizowania tego rodzaju danych.

> [!Important]
> Narzędzia diagnostyczne są obsługiwane dla rozwoju platformy .NET w programie Visual Studio, w tym ASP.NET i rozwoju macierzystego/C++.

W tym artykule omówimy analizowanie użycia procesora CPU w normalnym przepływie pracy debugowania. Można również analizować użycie procesora CPU bez dołączonego debugera lub kierowanie na uruchomioną aplikację. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Można również użyć innego narzędzia do profilowania, [Porady perf](../profiling/perftips.md), aby przejść przez kod i zidentyfikować, jak długo trwa określone funkcje lub bloki kodu, aby zakończyć.

Narzędzia profilowania można używać bez debugera w systemie Windows 7 i nowszych. System Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (okno**Narzędzia diagnostyczne).**

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Zbieranie danych dotyczących użycia procesora
> * Analizowanie danych użycia procesora

## <a name="step-1-collect-profiling-data"></a>Krok 1: Zbieranie danych profilowania

1. Otwórz projekt, który chcesz debugować w programie Visual Studio i ustaw punkt przerwania w aplikacji w punkcie, w którym chcesz sprawdzić użycie procesora CPU.

2. Ustaw drugi punkt przerwania na końcu funkcji lub regionu kodu, który chcesz analizować.

    Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, które chcesz analizować.

3. Okno **Narzędzia diagnostyczne** jest wyświetlane automatycznie, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij przycisk **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show .

4. Za pomocą ustawienia **Wybierz narzędzia** na pasku narzędzi można wybrać, czy ma być widoczne **użycie procesora CPU,** [użycie pamięci,](../profiling/Memory-Usage.md)czy oba te elementy. Jeśli korzystasz z programu Visual Studio Enterprise, można również włączyć lub wyłączyć funkcję IntelliTrace w**opcjach** >  **narzędzi** > **IntelliTrace**.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Będziemy głównie patrząc na wykorzystanie procesora, więc upewnij się, że **użycie procesora jest** włączone (jest domyślnie włączone).

5. Kliknij **przycisk Debugowanie** > **rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok Podsumowanie narzędzi diagnostycznych. Jeśli chcesz otworzyć okno, kliknij przycisk **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show .

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Wyszukiwanie i filtrowanie zdarzeń na karcie Narzędzia diagnostyczne w oknie](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania zostanie trafiony.

7. Gdy debuger jest wstrzymany, włącz zbieranie danych użycia procesora CPU, a następnie otwórz kartę **Użycie procesora CPU.**

     ![Narzędzia diagnostyczne umożliwiają profilowanie procesora](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfilowanie")

     Po **wybraniu opcji Zarejestruj profil procesora,** program Visual Studio rozpocznie rejestrowanie funkcji i czas ich wykonania. Można wyświetlić te dane zbierane tylko wtedy, gdy aplikacja jest zatrzymana w punkcie przerwania.

8. Naciśnij klawisz F5, aby uruchomić aplikację w drugim punkcie przerwania.

     Teraz masz teraz dane dotyczące wydajności dla aplikacji specjalnie dla regionu kodu, który działa między dwoma punktami przerwania.

     Profiler rozpoczyna przygotowywanie danych wątku. Poczekaj, aż się skończy.

     ![Narzędzia diagnostyczne do przygotowywania wątków](../profiling/media/diag-tools-preparing-data.png "DiagToolsPrzygotowanieWłaczki")

     Narzędzie Użycie procesora CPU wyświetla raport na karcie **Użycie procesora CPU.**

     ![Karta Użycie procesora cpu narzędzi diagnostycznych](../profiling/media/diag-tools-cpu-usage-tab.png "Karta DiagToolsCPUUsageTab")

9. Jeśli chcesz wybrać bardziej szczegółowy region kodu do analizy, wybierz region na osi czasu procesora CPU (musi to być region, który pokazuje dane profilowania).

     ![Narzędzia diagnostyczne Wybierając segment czasu](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     W tym momencie można rozpocząć analizowanie danych.

     > [!TIP]
     >  Podczas próby zidentyfikowania problemów z wydajnością należy podjąć wiele pomiarów. Wydajność naturalnie różni się od uruchomienia do uruchomienia, a ścieżki kodu zazwyczaj wykonywane wolniej przy pierwszym uruchomieniu z powodu jednorazowej pracy inicjowania, takich jak ładowanie bibliotek DLL, JIT metody kompilowania i inicjowania pamięci podręcznej. Biorąc wiele pomiarów, można uzyskać lepsze wyobrażenie o zakresie i medianie wyświetlanej metryki, co pozwala porównać po raz pierwszy w stosunku do wydajności stanu ustalonego obszaru kodu.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analizowanie danych użycia procesora

Zaleca się rozpoczęcie analizowania danych przez zbadanie listy funkcji w obszarze Użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy, a następnie przyjrzenie się każdej z nich.

1. Na liście funkcji sprawdź funkcje, które wykonują najwięcej pracy.

    ![Lista funkcji użycia procesora CPU narzędzia diagnostyczne](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunkctionList")

    > [!TIP]
    > Funkcje są wyświetlane w kolejności, począwszy od tych, którzy wykonują najwięcej pracy (nie są one w kolejności wywołania). Pomaga to szybko zidentyfikować najdłużej działające funkcje.

2. Na liście funkcji kliknij dwukrotnie jedną z funkcji aplikacji, która wykonuje dużo pracy.

    Po dwukrotnym kliknięciu funkcji w lewym okienku zostanie otwarty widok **Wywołujący/Wywoływany.**

    ![Diagnostyka Narzędzia Caller Callee Widok](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    W tym widoku wybrana funkcja jest wyświetlana w nagłówku i w polu **Bieżąca funkcja** (GetNumber, w tym przykładzie). Funkcja, która wywoływała bieżącą funkcję, jest wyświetlana po lewej stronie w obszarze **Funkcje wywołujące,** a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w polu **Nazywane funkcje** po prawej stronie. (Można wybrać do któregokolwiek z pól, aby zmienić bieżącą funkcję).

    Ten widok pokazuje całkowity czas (ms) i procent całkowitego czasu działania aplikacji, który został pobrany do wykonania.
    **Treść funkcji** pokazuje również całkowitą ilość czasu (i procent czasu) spędzoną w treści funkcji, z wyłączeniem czasu spędzonego podczas wywoływania i wywoływania funkcji. (W tym przykładzie 2367 z 2389 ms zostały wydane w treści funkcji, a pozostałe 22 ms zostały wydane w kodzie zewnętrznym wywoływane przez tę funkcję).

    > [!TIP]
    > Wysokie wartości w **treści funkcji** może wskazywać wąskie gardło wydajności w ramach samej funkcji.

3. Aby wyświetlić widok wyższego poziomu pokazujący kolejność wywoływania funkcji, wybierz pozycję **Drzewo wywołań** z listy rozwijanej u góry okienka.

    Każdy ponumerowany obszar na rysunku odnosi się do kroku w procedurze.

    ::: moniker range=">=vs-2019"
    ![Drzewo wywoławek narzędzi diagnostycznych](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree (DiagToolsCallTree)")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Drzewo wywoławek narzędzi diagnostycznych](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree (DiagToolsCallTree)")
    ::: moniker-end

    |||
    |-|-|
    |![Krok 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołań użycia procesora CPU jest pseudowęzkiem|
    |![Krok 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|W większości aplikacji, gdy opcja [Pokaż kod zewnętrzny](#view-external-code) jest wyłączona, węzeł drugiego poziomu jest węzłem **[Kod zewnętrzny],** który zawiera kod systemu i struktury, który uruchamia i zatrzymuje aplikację, rysuje interfejs użytkownika, kontroluje planowanie wątków i udostępnia inne usługi niskiego poziomu aplikacji.|
    |![Krok 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu są metody kodu użytkownika i procedur asynchronicznych, które są wywoływane lub tworzone przez system drugiego poziomu i kod struktury.|
    |![Krok 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko dla wywołań metody nadrzędnej. Gdy **opcja Pokaż kod zewnętrzny** jest wyłączona, metody aplikacji mogą również zawierać węzeł **[Kod zewnętrzny].**|

    Oto więcej informacji na temat wartości kolumn:

    - **Całkowita wartość procesora CPU** wskazuje, ile pracy wykonano przez funkcję i wszystkie funkcje wywoływane przez nią. Wysokie całkowite wartości procesora CPU wskazują na funkcje, które są ogólnie najdroższe.

    - **Self CPU** wskazuje, ile pracy zostało wykonane przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały wywołane przez niego. Wysokie wartości **procesora samoumiejenia procesora** CPU może wskazywać wąskie gardło wydajności w ramach samej funkcji.

    - **Moduły** Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [Kod zewnętrzny].

    ::: moniker range=">=vs-2019"
    Aby wyświetlić wywołania funkcji, które używają najwyższego odsetka procesora w widoku drzewa wywołań, kliknij przycisk **Rozwiń ścieżkę gorącą**.

    ![Ścieżka gorąca narzędzi diagnostycznych](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Jeśli widzisz kod w drzewie wywołań oznaczony jako "uszkodzony" kod lub "unwalkable stosu", oznacza to, że zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) prawdopodobnie zostały usunięte. Spróbuj zebrać ten sam ślad po raz drugi, aby rozwiązać ten problem.

## <a name="view-external-code"></a>Wyświetl kod zewnętrzny

Kod zewnętrzny to funkcje w składnikach systemu i struktury, które są wykonywane przez kod, który piszesz. Kod zewnętrzny obejmują funkcje, które uruchamiają i zatrzymują aplikację, rysują interfejs użytkownika, kontrolują wątki i udostępniają inne usługi niskiego poziomu do aplikacji. W większości przypadków nie będzie zainteresowany kodem zewnętrznym, a więc narzędzie użycie procesora CPU zbiera funkcje zewnętrzne metody użytkownika w jednym węźle **[Kod zewnętrzny].**

Jeśli chcesz wyświetlić ścieżki połączeń kodu zewnętrznego, wybierz pozycję **Pokaż kod zewnętrzny** z listy **widoku Filtruj,** a następnie wybierz pozycję **Zastosuj**.

![Wybierz pozycję Widok filtru, a następnie pokaż kod zewnętrzny](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowEksternalny kod")

Należy pamiętać, że wiele zewnętrznych łańcuchów wywołań kodu są głęboko zagnieżdżone, tak, że szerokość funkcji name kolumny może przekroczyć szerokość wyświetlania wszystkich, ale największy monitorów komputera. W takim przypadku nazwy funkcji są wyświetlane jako **[...]**.

Użyj pola wyszukiwania, aby znaleźć węźle, którego szukasz, a następnie użyj poziomego paska przewijania, aby wyświetlić dane.

> [!TIP]
> Jeśli profil zewnętrzny kod, który wywołuje funkcje systemu Windows, należy upewnić się, że masz najbardziej aktualne . *plików pdb.* Bez tych plików widoki raportu będą wyświetlać nazwy funkcji systemu Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji na temat tego, jak upewnić się, że masz potrzebne pliki, zobacz [Określanie symbolu (pdb) i plików źródłowych w debugerze](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak zbierać i analizować dane użycia procesora CPU. Jeśli ukończono już [pierwsze spojrzenie na narzędzia profilowania,](../profiling/profiling-feature-tour.md)możesz szybko przyjrzeć się, jak analizować użycie pamięci w aplikacjach.

> [!div class="nextstepaction"]
> [Użycie pamięci profilu w programie Visual Studio](../profiling/memory-usage.md)
