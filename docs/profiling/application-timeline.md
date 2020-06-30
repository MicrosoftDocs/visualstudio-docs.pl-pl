---
title: Analizowanie użycia zasobów w aplikacjach XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 0bb76de0d62ab504090d9ac1864ba7ee5627f69d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537283"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analizowanie użycia zasobów i działania wątku interfejsu użytkownika (XAML)

Użyj profilera **oś czasu aplikacji** , aby znaleźć i rozwiązać problemy z wydajnością związane z interakcją aplikacji w aplikacjach XAML. To narzędzie pomaga ulepszyć wydajność aplikacji XAML, pokazując szczegółowy widok użycia zasobów aplikacji. Można analizować czas spędzony przez aplikację przygotowującą ramki interfejsu użytkownika (układ i renderowanie), obsługiwać żądania sieci i dysku, a także w scenariuszach takich jak uruchamianie aplikacji, ładowanie stron i zmiana rozmiaru systemu Windows.

**Oś czasu aplikacji** jest jednym z narzędzi, które można uruchomić przy użyciu **Debug**  >  **profilera wydajności** debugowania.

To narzędzie zastępuje narzędzie czasu **odpowiedzi interfejsu użytkownika XAML** , które było częścią zestawu narzędzi diagnostycznych dla Visual Studio 2013.

Tego narzędzia można użyć na następujących platformach:

- Aplikacje uniwersalne systemu Windows (w systemie Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.NET 4,0 i nowsze)
- Windows 7

> [!NOTE]
> Dane użycia procesora CPU i dane zużycia energii można zbierać i analizować wraz z danymi **ApplicationTimeline** . Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="collect-application-timeline-data"></a>Zbierz dane osi czasu aplikacji

Możesz profilować czas odpowiedzi aplikacji na komputerze lokalnym, podłączonym urządzeniu, symulatorze programu Visual Studio lub emulatorach lub urządzeniu zdalnym. Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Jeśli to możliwe, uruchom aplikację bezpośrednio na urządzeniu. Wydajność aplikacji zaobserwowanej w symulatorze lub za pomocą połączenia pulpitu zdalnego może nie być taka sama jak Rzeczywista wydajność na urządzeniu. Z drugiej strony zbieranie danych przy użyciu narzędzi zdalnych programu Visual Studio nie ma wpływu na dane wydajności.

Poniżej przedstawiono podstawowe kroki:

1. Otwórz aplikację XAML.

2. Kliknij pozycję **Debuguj/Performance Profiler**. W oknie. diagsession powinna zostać wyświetlona lista narzędzi profilowania.

3. Wybierz **oś czasu aplikacji** a następnie kliknij przycisk **Rozpocznij** u dołu okna.

   ![Wybrane narzędzie Oś czasu aplikacji](../profiling/media/apptimelineselect.png "Narzędzie Oś czasu aplikacji")

   > [!NOTE]
   > Może zostać wyświetlone okno Kontrola konta użytkownika z prośbą o zgodę na uruchomienie *VsEtwCollector.exe*. Kliknij przycisk **tak**.

4. Uruchom scenariusz, który interesuje Cię w aplikacji, aby zbierać dane dotyczące wydajności.

5. Aby zatrzymać profilowanie, przełącz się z powrotem do okna. diagsession, a następnie kliknij przycisk **Zatrzymaj** u góry okna.

   Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

   ![Raport profilera osi czasu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analizowanie danych profilowania osi czasu

Po zebraniu danych profilowania można wykonać poniższe kroki, aby rozpocząć analizę:

1. Wyświetl informacje w wykresach **wykorzystanie wątku interfejsu użytkownika** i **przepływność wizualna (FPS)** , a następnie użyj pasków nawigacyjnych osi czasu, aby wybrać zakres czasu, który chcesz przeanalizować.

2. Korzystając z informacji w wykresach **użycia wątku interfejsu użytkownika** lub **przepływności wizualizacji (FPS)** , sprawdź szczegóły w widoku **szczegóły osi czasu** , aby znaleźć możliwe przyczyny dowolnego pozornego braku odpowiedzi.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Scenariusze raportów, kategorie i zdarzenia

Narzędzie **oś czasu aplikacji** wyświetla dane chronometrażu dla scenariuszy, kategorii i zdarzeń, które są związane z wydajnością XAML.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Oś czasu sesji diagnostycznej

![Oś czasu wydajności i diagnostyki](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Linijka w górnej części strony pokazuje oś czasu profilowanych informacji. Ta oś czasu ma zastosowanie do wykresu **wykorzystania wątków interfejsu użytkownika** i wykresu **przepływności wizualnej** . Można zawęzić zakres raportu, przeciągając paski nawigacyjne na osi czasu w celu zaznaczenia segmentu osi czasu.

Na osi czasu są również wyświetlane wszystkie znaczniki użytkownika, które zostały wstawione, oraz zdarzenia cyklu życia aktywacji aplikacji.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>Wykres wykorzystania wątku interfejsu użytkownika

![Wykres wykorzystania CPU](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

Wykres **wykorzystanie wątku interfejsu użytkownika (%)** to wykres słupkowy, który wyświetla względną ilość czasu spędzoną w kategorii dla zakresu kolekcji.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Wykres przepływności wizualizacji (FPS)

![Wykres przepływności wizualizacji](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

Wykres liniowy **przepływności (FPS)** pokazuje klatki na sekundę (FPS) w interfejsie użytkownika i wątku kompozycji dla aplikacji.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Szczegóły osi czasu

Widok szczegółów polega na tym, że spędzasz najwięcej czasu na analizowanie raportu. Pokazuje użycie procesora przez aplikację według podsystemu Framework interfejsu użytkownika lub składnika systemowego, który zużywał procesor CPU.

Obsługiwane są następujące zdarzenia:

|Nazwa|Opis|
|-|-|
|**Asax**|Czas poświęcony na analizowanie plików XAML i tworzenie obiektów.<br /><br /> Rozwijanie węzła **analizy** w **szczegółach osi czasu** wyświetla łańcuch zależności wszystkich plików XAML, które zostały przeanalizowane ze względu na zdarzenie główne. Ta Porada umożliwia zidentyfikowanie niepotrzebnych analiz plików i tworzenie obiektów w scenariuszach z uwzględnieniem wydajności i ich optymalizację.|
|**Layout**|W dużych aplikacjach, tysiące elementów mogą być wyświetlane na ekranie w tym samym czasie. To wyświetlenie może spowodować niską szybkość klatek interfejsu użytkownika i odpowiadające im niewystarczająca czas odpowiedzi aplikacji. Zdarzenie układu dokładnie określa koszt zniesienia poszczególnych elementów (to znaczy czas spędzony w rozmieszczeniu, mierze, ApplyTemplate, ArrangeOverride i MeasureOverride). Kompiluje także drzewa wizualne, które uczestniczyły w przejściu do układu. Możesz użyć tej wizualizacji, aby określić, które drzewa logiczne mają być oczyszczane, lub aby oszacować inne mechanizmy odroczenia, aby zoptymalizować przebieg układu.|
|**Renderowanie**|Czas spędzony na rysowaniu elementów XAML na ekranie.|
|**I/0**|Czas poświęcony na pobieranie danych z dysku lokalnego lub z zasobów sieciowych, do których dostęp odbywa się za pośrednictwem [interfejsu API Microsoft Windows Internet (WinInet)](/windows/desktop/WinInet/portal).|
|**Kod aplikacji**|Czas spędzony na wykonywaniu kodu aplikacji (użytkownika), który nie jest związany z analizowaniem ani układem.|
|**Inne XAML**|Czas poświęcony na wykonanie kodu środowiska uruchomieniowego XAML.|

> [!TIP]
> Wybierz narzędzie **użycie procesora CPU** wraz z **oś czasu aplikacji** narzędziem po rozpoczęciu profilowania, aby wyświetlić metody aplikacji wykonywane w wątku interfejsu użytkownika. Przeniesienie długotrwałego kodu aplikacji do wątku w tle może poprawić czas odpowiedzi interfejsu użytkownika.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Dostosowywanie szczegółów osi czasu

Pasek narzędzi **szczegóły osi czasu** umożliwia sortowanie, filtrowanie i określanie adnotacji wpisów widoku **szczegółów osi czasu** .

|Nazwa|Opis|
|-|-|
|**Sortuj według**|Sortuj według czasu rozpoczęcia lub długości zdarzeń.|
|![Grupuj zdarzenia według ramki](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Dodaje lub usuwa kategorię **ramek** najwyższego poziomu, która grupuje zdarzenia według ramki.|
|![Filtruj listę szczegółów osi czasu](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtruje listę według wybranych kategorii i długości zdarzeń.|
|![Dostosuj informacje szczegółowe dotyczące osi czasu](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umożliwia określenie adnotacji do zdarzeń.|

## <a name="see-also"></a>Zobacz też

- [Blog zespołu WPF: nowe narzędzie do analizy wydajności interfejsu użytkownika dla aplikacji WPF](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)
- [Najlepsze rozwiązania w zakresie wydajności dla aplikacji platformy UWP przy użyciu języków C++, C# i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optymalizowanie wydajności aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
