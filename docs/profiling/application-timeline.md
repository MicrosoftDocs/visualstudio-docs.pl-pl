---
title: Analizowanie zużycia zasobów w aplikacjach XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a368a9b8f6d25753993a2cc10ea9ca94734d6709
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128288"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analizowanie zużycia zasobów i aktywności wątku interfejsu użytkownika (XAML)

Profiler **osi czasu aplikacji** służy do znajdowania i rozwiązywania problemów z wydajnością związanych z interakcją aplikacji w aplikacjach XAML. To narzędzie pomaga zwiększyć wydajność aplikacji XAML, wyświetlając szczegółowy widok zużycia zasobów aplikacji. Można analizować czas spędzony przez aplikację przygotowując ramki interfejsu użytkownika (układ i renderowanie), obsługę żądań sieciowych i dysków oraz w scenariuszach takich jak Uruchamianie aplikacji, Ładowanie strony i rozmiar systemu Windows.

**Oś czasu aplikacji** jest jednym z narzędzi, które można uruchomić z **debugowania** > **wydajności profiler** polecenia.

To narzędzie zastępuje narzędzie **do reagowania interfejsu użytkownika XAML,** które było częścią zestawu narzędzi diagnostycznych dla programu Visual Studio 2013.

Tego narzędzia można używać na następujących platformach:

- Uniwersalne aplikacje systemu Windows (w systemie Windows 10)
- Windows 8.1
- Podstawa prezentacji systemu Windows (.Net 4.0 lub powyżej)
- Windows 7

> [!NOTE]
> Można zbierać i analizować dane użycia procesora CPU i dane zużycia energii wraz z danymi **ApplicationTimeline.** Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="collect-application-timeline-data"></a>Zbieranie danych osi czasu aplikacji

Szybkość reakcji aplikacji można profilować na komputerze lokalnym, podłączonym urządzeniu, symulatorze lub emulatorach programu Visual Studio lub urządzeniu zdalnym. Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Jeśli to możliwe, uruchom aplikację bezpośrednio na urządzeniu. Wydajność aplikacji obserwowana w symulatorze lub za pośrednictwem połączenia pulpitu zdalnego może nie być taka sama jak rzeczywista wydajność urządzenia. Z drugiej strony zbieranie danych przy użyciu narzędzi zdalnych programu Visual Studio nie wpływa na dane dotyczące wydajności.

Poniżej przedstawiono podstawowe kroki:

1. Otwórz aplikację XAML.

2. Kliknij **przycisk Debugowanie / Profiler wydajności**. W oknie .diagsession powinna zostać wyświetlona lista narzędzi profilowania.

3. Wybierz **pozycję Oś czasu aplikacji,** a następnie kliknij przycisk **Start** u dołu okna.

   > [!NOTE]
   > Może zostać wyświetlene okno Kontrola konta użytkownika z prośbą o zgodę na uruchomienie *pliku VsEtwCollector.exe*. Kliknij **przycisk Tak**.

4. Uruchom scenariusz, który cię interesuje profilowanie w aplikacji, aby zbierać dane o wydajności.

5. Aby zatrzymać profilowanie, przełącz się z powrotem do okna .diagsession i kliknij przycisk **Zatrzymaj** w górnej części okna.

   Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

   ![Raport profilera osi czasu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analizowanie danych profilowania osi czasu

Po zebraniu danych profilowania można wykonać poniższe kroki, aby rozpocząć analizę:

1. Wyświetl informacje na wykresach **wykorzystania wątku interfejsu użytkownika** i **przepływności wizualnej (FPS),** a następnie użyj pasków nawigacyjnych osi czasu, aby wybrać zakres czasu, który chcesz przeanalizować.

2. Korzystając z informacji w **wykorzystaniu wątku interfejsu** użytkownika lub **wizualnej przepływności (FPS)** wykresy, sprawdź szczegóły w widoku **szczegółów osi czasu,** aby znaleźć możliwe przyczyny pozornego braku reakcji.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Scenariusze raportów, kategorie i zdarzenia

**Narzędzie Oś czasu aplikacji** wyświetla dane chronometrażu dla scenariuszy, kategorii i zdarzeń związanych z wydajnością XAML.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Oś czasu sesji diagnostycznej

![Oś czasu wydajności i diagnostyki](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Linijka w górnej części strony pokazuje oś czasu dla profilowanych informacji. Ta oś czasu ma zastosowanie zarówno do **wykresu wykorzystania wątku interfejsu** użytkownika, jak i wykresu **przepływności wizualnej.** Można zawęzić zakres raportu, przeciągając paski nawigacyjne na osi czasu w celu zaznaczenia segmentu osi czasu.

Na osi czasu są również wyświetlane wszystkie wstawione znaczniki użytkownika oraz zdarzenia cyklu życia aktywacji aplikacji.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>Wykres wykorzystania wątku interfejsu użytkownika

![Wykres wykorzystania procesora CPU](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

**Wykres wykorzystania wątku interfejsu użytkownika (%)** jest wykresem słupkowym, który wyświetla względną ilość czasu spędzonego w kategorii podczas zakresu kolekcji.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Wykres przepływności wizualnej (FPS)

![Wykres przepływności wizualnej](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

Wykres linii **przepływności wizualnej (FPS)** pokazuje klatki na sekundę (FPS) w wątku interfejsu użytkownika i kompozycji dla aplikacji.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Szczegóły osi czasu

Widok szczegółów to miejsce, w którym spędzasz większość czasu na analizowaniu raportu. Pokazuje użycie procesora CPU przez aplikację sklasyfikowane przez podsystem struktury interfejsu użytkownika lub składnik systemu, który korzystał z procesora CPU.

Obsługiwane są następujące zdarzenia:

|||
|-|-|
|**Analizowania**|Czas poświęcony na analizowanie plików XAML i tworzenie obiektów.<br /><br /> Rozwijanie węzła **analizowania** w **szczegółach osi czasu** wyświetla łańcuch zależności wszystkich plików XAML, które zostały przeanalizowane z powodu zdarzenia głównego. Ta wskazówka umożliwia identyfikowanie niepotrzebnych analizowania plików i tworzenia obiektów w scenariuszach uwzględniających wydajność i optymalizowanie ich.|
|**Układ**|W dużych aplikacjach tysiące elementów mogą być wyświetlane na ekranie w tym samym czasie. Ten wyświetlacz może spowodować niską liczbę klatek na sekundę interfejsu użytkownika i odpowiednio słabą szybkość reakcji aplikacji. Zdarzenie Układ dokładnie określa koszt układania każdego elementu (czyli czas spędzony w Rozmieszczeniu, Miara, ZastosujTemplate, ArrangeOverride i MeasureOverride). Buduje również drzewa wizualne, które brały udział w układzie pass. Ta wizualizacja służy do określenia, które drzewa logiczne do przycinania lub do oceny innych mechanizmów odroczenia w celu optymalizacji przebiegu układu.|
|**Renderowanie**|Czas poświęcony na rysowanie elementów XAML na ekranie.|
|**I/0**|Czas poświęcony na pobieranie danych z dysku lokalnego lub z zasobów sieciowych, do których uzyskuje się dostęp za pośrednictwem [interfejsu API Sieci Microsoft Windows (WinINet).](/windows/desktop/WinInet/portal)|
|**Kod aplikacji**|Czas spędzony na wykonywaniu kodu aplikacji (użytkownika), który nie jest związany z analizowaniem lub układem.|
|**Xaml Inne**|Czas spędzony na wykonywaniu kodu środowiska wykonawczego XAML.|

> [!TIP]
> Wybierz narzędzie **Użycie procesora CPU** wraz z narzędziem **Osi czasu aplikacji** po uruchomieniu profilowania, aby wyświetlić metody aplikacji, które są wykonywane w wątku interfejsu użytkownika. Przenoszenie długotrwałego kodu aplikacji do wątku w tle może poprawić szybkość reakcji interfejsu użytkownika.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Dostosowywanie szczegółów osi czasu

Pasek narzędzi **Szczegóły osi czasu** służy do sortowania, filtrowania i określania adnotacji wpisów widoku szczegółów osi **czasu.**

|||
|-|-|
|**Sortuj według**|Sortuj według czasu rozpoczęcia lub długości zdarzeń.|
|![Grupowanie zdarzeń według ramek](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Dodaje lub usuwa kategorię **ramki** najwyższego poziomu, która grupuje zdarzenia według ramek.|
|![Lista szczegółów oś czasu filtrowania](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtruje listę według wybranych kategorii i długości zdarzeń.|
|![Dostosowywanie informacji o szczegółach osi czasu](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umożliwia określenie adnotacji zdarzeń.|

## <a name="see-also"></a>Zobacz też

- [Blog zespołu WPF: Nowe narzędzie do analizy wydajności interfejsu użytkownika dla aplikacji WPF](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)
- [Najważniejsze wskazówki dotyczące wydajności aplikacji platformy uniwersalnej systemu Windows w językach C++, C#i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optymalizacja wydajności aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
