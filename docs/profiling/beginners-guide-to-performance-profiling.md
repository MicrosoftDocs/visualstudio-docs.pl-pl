---
title: Użycie pomiar procesora CPU w twoich aplikacjach
description: Analizuj problemy z wydajnością procesora CPU w aplikacji za pomocą narzędzia diagnostyczne zintegrowane z debugerem.
ms.custom: seodec18
ms.date: 02/27/2017
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed0549cceb928b622578add5a634bb5795e5c96d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889793"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Miara wydajności aplikacji, analizując użycie procesora CPU
Za pomocą programu Visual Studio profiling tools do analizowania problemów z wydajnością w aplikacji. Poniższa procedura przedstawia sposób użycia **użycie procesora CPU** karta Narzędzia diagnostyczne, aby uzyskać dane wydajności dotyczące Twojej aplikacji. Narzędzia diagnostyczne są obsługiwane podczas tworzenia aplikacji .NET w programie Visual Studio, w tym usługi ASP.NET i dla rozwoju natywnego/C++.
  
Gdy debuger zatrzymuje, **użycie procesora CPU** Narzędzie gromadzi informacje o funkcjach, które są wykonywane w aplikacji. Narzędzie wyświetla listę funkcji, które zostały wykonując pracę i zawiera wykres osi czasu, w którym można skupić się na poszczególnych segmentach sesji pobierania próbek.

Centrum diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** nie oferują danych, których potrzebują, [innych narzędzi do profilowania](../profiling/profiling-feature-tour.md) zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. W wielu przypadkach wąskich gardeł wydajności aplikacji może być spowodowane przez coś innego niż Procesora, takich jak pamięć, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji rejestracji i analizowaniu tego rodzaju danych.

| | |
|---------|---------|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) na temat korzystania z narzędzia diagnostyczne, które pokazuje sposób analizowanie użycia procesora CPU oraz analizowanie użycia pamięci. |

W tym artykule omówimy Analizowanie użycia procesora CPU w normalnym przepływie pracy debugowania. Możesz również Analizowanie użycia procesora CPU bez debugera dołączone lub stosując uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchamianie narzędzi z lub bez debugeraprofilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Można użyć narzędzi profilowania bez debugera, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno).

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Zbieranie danych użycia procesora CPU
> * Analizowanie danych użycia procesora CPU
  
## <a name="step-1-collect-profiling-data"></a>Krok 1. Zbieranie danych profilowania 
  
1.  Otwórz projekt, który chcesz debugować w programie Visual Studio i ustaw punkt przerwania w swojej aplikacji w punkcie, w którym chcesz sprawdzić użycie procesora CPU.

2.  Ustaw drugi punkt przerwania na końcu funkcji lub regionu kod, który chcesz analizować.

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz analizować.
  
3.  **Narzędzia diagnostyczne** okno pojawia się automatycznie, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

4.  Można wybrać, czy wyświetlane są **użycie procesora CPU**, [użycie pamięci](../profiling/Memory-Usage.md), lub oba z **wybierz narzędzia** ustawienie na pasku narzędzi. Jeśli używasz programu Visual Studio Enterprise można również włączyć lub wyłączyć IntelliTrace w **narzędzia** > **opcje** > **IntelliTrace**.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     Firma Microsoft będzie przede wszystkim należy spojrzenie na wykorzystanie procesora CPU, więc upewnij się, że **użycie procesora CPU** jest włączona (jest włączony domyślnie).

5.  Kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok podsumowania narzędzia diagnostyczne.

     ![Karta Podsumowanie narzędzia do diagnostyki](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     Aby uzyskać więcej informacji na temat zdarzeń, zobacz [wyszukiwanie i filtrowanie na karcie zdarzenia w oknie narzędzia diagnostyczne](https://blogs.msdn.microsoft.com/devops/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6.  Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania na.

7.  Gdy debuger jest wstrzymany, Włącz zbieranie danych użycia procesora CPU, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyczne Włącz profilowanie procesora CPU](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     Po wybraniu **profil procesora CPU rekordu**, Visual Studio spowoduje rozpoczęcie rejestrowania funkcji i czas, jaki przyjmują do wykonania. Ta zebrane dane może wyświetlać tylko w przypadku, gdy aplikacja jest zatrzymywane w punkcie przerwania.

8.  Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane wydajności dla twojej aplikacji specjalnie dla regionu kodu wykonywanego między dwoma punktami przerwania.

9.  Wybierz region interesuje Cię analizowanie na osi czasu Procesora (musi to być region, który pokazuje dane profilowania).

     ![Narzędzia diagnostyczne, wybierając pozycję Segment czasu](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     Program profilujący rozpoczyna, przygotowywanie danych wątku. Poczekaj na zakończenie jego działania.

     ![Trwa przygotowywanie wątków narzędzia do diagnostyki](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     Narzędzie użycie procesora CPU wyświetla raport w **użycie procesora CPU** kartę.
  
     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     W tym momencie można rozpocząć analizy danych.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2. Analizowanie danych użycia procesora CPU

Zaleca się rozpocząć analizowanie danych, sprawdzając listę funkcji, w obszarze użycie procesora CPU, identyfikowanie funkcji, które wykonują najwięcej pracy i następnie wykonywanie bliższe spojrzenie na każdym z nich.

1. Na liście funkcji zbadać funkcje, które wykonują najwięcej pracy.

    ![Diagnostyka narzędzia użycie procesora CPU, lista funkcji](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od osoby faktycznie wykonujące najwięcej pracy (nie są w kolejności wywołań). Dzięki temu można szybko zidentyfikować najdłuższy uruchomionej funkcji.

2. Na liście funkcji dwukrotnie kliknij funkcji aplikacji, które są w sposób pracy.

    Po dwukrotnym kliknięciu funkcję **wywołujący/wywoływany** w okienku po lewej stronie zostanie otwarty widok. 

    ![Widok wywoływany obiekt wywołujący narzędzia do diagnostyki](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji pojawia się w nagłówku i w **bieżącą funkcję** pole (w tym przykładzie GetNumber). Funkcja, która wywołała bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, oraz wszelkie funkcje wywołane przez bieżącą funkcję są pokazane w **funkcji o nazwie** pole po prawej stronie. (Możesz wybrać jedno z pól można zmienić bieżącej funkcji.)

    Ten widok przedstawia łączny czas (ms) i procent ogólnej aplikacji, czas, który funkcji zostały podjęte w celu ukończenia działania.
    **Funkcja treści** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. (W tym przykładzie ms 3713 poza 3729 spędzono w treści funkcji, a pozostałe 16 ms spędzono w kodzie zewnętrznych wywoływanych przez tę funkcję).

    > [!TIP]
    > O wysokiej wartości w **treści funkcji** może wskazać wąskie gardło w samej funkcji.

3. Jeśli chcesz wyświetlić widok wyższego poziomu, przedstawiający kolejność, w którym funkcje są wywoływane, wybierz opcję **drzewo wywołań** z listy rozwijanej w górnej części okienka.
 
    Każdy ponumerowany obszar na rysunku dotyczy kroku procedury.
  
    ![Narzędzia diagnostyczne drzewo wywołań](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![Krok 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołanie użycie procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|W przypadku większości aplikacji gdy [Pokaż kod zewnętrzny](#view-external-code) opcja jest wyłączona, węzeł drugiego poziomu, który jest **[kod zewnętrzny]** węzeł zawierający system i platforma kod, który uruchamia i zatrzymuje aplikację, rysuje interfejsu użytkownika kontroluje planowanie wątków i zapewnia inne niskopoziomowe usługi dla aplikacji.|  
|![Krok 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu są asynchroniczne procedur, które są nazywane lub utworzonych przez system drugiego poziomu oraz kodu struktury i metody kod użytkownika.|
|![Krok 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|

Poniżej przedstawiono więcej informacji na temat wartości kolumny:

- **Łączna liczba Procesora** wskazuje, ile pracy zostało wykonanej przez funkcję i wszystkie funkcje wywoływane przez nią. Wysokiej wartości sumy procesora CPU wskazuje funkcje, które są najbardziej kosztowne.
  
- **Czas własny Procesora** wskazuje, ile pracy zostało wykonanej przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały przez nią wywołane. Wysoka **procesor CPU samodzielnie** wartości może wskazać wąskie gardło w samej funkcji.

- **Moduły** nazwę modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].

## <a name="view-external-code"></a>Pokaż kod zewnętrzny

Kod zewnętrzny są funkcje w system i platforma składników, które są wykonywane przez tworzonego kodu. Kod zewnętrzny obejmują funkcje, które Uruchom i Zatrzymaj aplikację, narysuj interfejsu użytkownika, kontrolować wątki i podaj inne niskopoziomowe usługi dla aplikacji. W większości przypadków nie będzie zainteresowani kod zewnętrzny, a więc narzędzie użycie procesora CPU w jednym zbiera funkcji zewnętrznych metody użytkownika **[kod zewnętrzny]** węzła.
  
Aby wyświetlić wywołania ścieżek kodu zewnętrznego, należy wybrać **Pokaż kod zewnętrzny** z **filtrowania widoku** listy, a następnie wybierz **Zastosuj**.  
  
![Wybierz Widok filtrów, a następnie Pokaż kod zewnętrzny](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
Należy pamiętać, że wiele łańcuchy wywołania kodu zewnętrznego głęboko zagnieżdżone, tak, aby szerokość kolumny nazwy funkcji może być dłuższa niż szerokość wyświetlanie wszystkich pól poza największych monitorów komputera. W takim wypadku nazwy funkcji są wyświetlane jako **[...]** .
  
Użyj pola wyszukiwania, aby odnaleźć węzła, którego szukasz, a następnie użyj poziomych pasków przewijania do przenoszenia danych do wyświetlenia.

> [!TIP]
> Jeśli profilowany kod zewnętrzny, która wywołuje funkcje Windows, należy upewnić się, że najbardziej aktualnej. *pdb* plików. Bez tych plików widok raportu wyświetli listę nazw funkcji Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji na temat upewnij się, że pliki potrzebne Ci zobacz [określanie plików symboli (.pdb) i plików źródłowych w debugerze](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób zbieranie i analizowanie danych użycia procesora CPU. Jeśli znasz już [Pierwsze spojrzenie na profilowanie narzędzia](../profiling/profiling-feature-tour.md), możesz chcieć uzyskać krótkie omówienie sposobu analizowania użycia pamięci w aplikacjach.

> [!div class="nextstepaction"]
> [Użycie pamięci profilu w programie Visual Studio](../profiling/memory-usage.md) 
