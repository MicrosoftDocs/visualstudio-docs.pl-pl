---
title: Analizowanie zużycia zasobów w aplikacjach XAML
description: Użyj profilera Oś czasu aplikacji, aby znaleźć problemy z wydajnością w aplikacjach XAML. Możesz analizować czas spędzony na różnych zadaniach w różnych scenariuszach.
ms.custom: SEO-VS-2020
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d352c118bd8b21b9dcbf62f7dd32eaf2999ed471
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388025"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analizowanie użycia zasobów i działania wątku interfejsu użytkownika (XAML)

Profiler **aplikacji Oś czasu aplikacji,** aby znaleźć i rozwiązać problemy z wydajnością związane z interakcjami aplikacji w aplikacjach XAML. To narzędzie pomaga zwiększyć wydajność aplikacji XAML, wyświetlając szczegółowy widok użycia zasobów aplikacji. Możesz przeanalizować czas spędzony przez aplikację na przygotowaniu ramek interfejsu użytkownika (układ i renderowanie), obsłudze żądań sieci i dysków oraz w scenariuszach takich jak uruchamianie aplikacji, ładowanie strony i zmiana rozmiaru systemu Windows.

**Oś czasu aplikacji** to jedno z narzędzi, które można uruchomić za pomocą polecenia **Profiler wydajności**  >   debugowania.

To narzędzie zastępuje narzędzie **czasu odpowiedzi interfejsu** użytkownika XAML, które było częścią zestawu narzędzi diagnostycznych dla Visual Studio 2013.

Tego narzędzia można używać na następujących platformach:

- Aplikacje uniwersalne systemu Windows (w Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 i więcej)
- Windows 7

> [!NOTE]
> Możesz zbierać i analizować dane użycia procesora CPU oraz dane dotyczące zużycia energii wraz z **danymi applicationTimeline.** Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

## <a name="collect-application-timeline-data"></a>Zbieranie danych osi czasu aplikacji

Czas odpowiedzi aplikacji można profilować na komputerze lokalnym, urządzeniu połączonym, Visual Studio symulatorze, emulatorach lub urządzeniu zdalnym. Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

> [!TIP]
> Jeśli to możliwe, uruchom aplikację bezpośrednio na urządzeniu. Wydajność aplikacji zaobserwowana w symulatorze lub za pośrednictwem połączenia pulpitu zdalnego może nie być taka sama jak rzeczywista wydajność urządzenia. Z drugiej strony zbieranie danych przy użyciu narzędzia Visual Studio Remote Tools nie wpływa na dane dotyczące wydajności.

Poniżej przedstawiono podstawowe kroki:

1. Otwórz aplikację XAML.

2. Kliknij **pozycję Debuguj/profiler wydajności**. W oknie .diagsession powinna zostać wyświetlona lista narzędzi profilowania.

3. Wybierz **Oś czasu aplikacji** a następnie kliknij przycisk **Start** w dolnej części okna.

   ![Oś czasu aplikacji wybrane narzędzie](../profiling/media/apptimelineselect.png "Oś czasu aplikacji narzędzi")

   > [!NOTE]
   > Może zostać otwarte okno Kontrola konta użytkownika z żądaniem uprawnień do uruchomienia *VsEtwCollector.exe*. Kliknij przycisk **Yes** (Tak).

4. Uruchom scenariusz, w którym chcesz profilować aplikację w celu zbierania danych dotyczących wydajności.

5. Aby zatrzymać profilowanie, wróć do okna .diagsession i kliknij pozycję **Zatrzymaj** w górnej części okna.

   Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

   ![Raport profilera osi czasu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analizowanie danych profilowania osi czasu

Po zebraniu danych profilowania można wykonać poniższe kroki, aby rozpocząć analizę:

1. Wyświetl informacje w  wykresach wykorzystania wątku interfejsu użytkownika i przepływności wizualnej **(PRZEPŁYWNOŚĆ wizualna),** a następnie użyj pasków nawigacji osi czasu, aby wybrać zakres czasu, który chcesz przeanalizować.

2. Korzystając z informacji  w grafach wykorzystania wątku interfejsu użytkownika  lub wizualnych przepływności **(CPU, Visual Throughput),** sprawdź szczegóły w widoku szczegóły osi czasu, aby znaleźć możliwe przyczyny jakichkolwiek braków czasu odpowiedzi.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a> Scenariusze, kategorie i zdarzenia raportów

Narzędzie **Oś czasu aplikacji** wyświetla dane chronometrażu dla scenariuszy, kategorii i zdarzeń związanych z wydajnością XAML.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a> Oś czasu sesji diagnostycznej

![Oś czasu wydajności i diagnostyki](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Linijka w górnej części strony pokazuje oś czasu profilowane informacje. Ta oś czasu dotyczy zarówno wykresu wykorzystania **wątku interfejsu** użytkownika, jak i wykresu **przepływności Wizualizacja.** Można zawęzić zakres raportu, przeciągając paski nawigacyjne na osi czasu w celu zaznaczenia segmentu osi czasu.

Na osi czasu są również wyświetlane wstawione znaczniki użytkownika oraz zdarzenia cyklu życia aktywacji aplikacji.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a> Wykres wykorzystania wątku interfejsu użytkownika

![Wykres wykorzystania CPU](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

Wykres **wykorzystania wątków interfejsu** użytkownika (%) jest wykresem słupkowym, który przedstawia względną ilość czasu spędzonego w kategorii w okresie kolekcji.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a> Wykres przepływności wizualnej (PRZEPŁYWNOŚĆ)

![Wizualny wykres przepływności](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

Wykres **liniowy przepływności wizualnej (JEDNOSTKI)** przedstawia ramki na sekundę w interfejsie użytkownika i wątek kompozycji dla aplikacji.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a> Szczegóły osi czasu

Widok szczegółów to miejsce, w którym większość czasu poświęcasz na analizowanie raportu. Pokazuje on użycie procesora CPU przez aplikację skategoryzowaną przez podsystem struktury interfejsu użytkownika lub składnik systemowy, który zużywa procesor CPU.

Obsługiwane są następujące zdarzenia:

|Nazwa|Opis|
|-|-|
|**Analizowania**|Czas spędzony na analizowaniu plików XAML i tworzeniu obiektów.<br /><br /> Rozwinięcie węzła **analizowania**  w szczegółach osi czasu powoduje wyświetlenie łańcucha zależności wszystkich plików XAML, które zostały analizowane z powodu zdarzenia głównego. Ta porada pozwala zidentyfikować niepotrzebne analizowanie plików i tworzenie obiektów w scenariuszach wrażliwych na wydajność i zoptymalizować je.|
|**Układ**|W dużych aplikacjach na ekranie mogą być jednocześnie wyświetlane tysiące elementów. Ten ekran może spowodować niską szybkość klatek interfejsu użytkownika i odpowiednio niską szybkość reakcji aplikacji. Zdarzenie Układ dokładnie określa koszt układu każdego elementu (czyli czas spędzony w układzie, mierze, ApplyTemplate, ArrangeOverride i MeasureOverride). Tworzy również drzewa wizualne, które brały udział w przebiegu układu. Ta wizualizacja umożliwia określenie drzew logicznych do przesłonić lub ocenę innych mechanizmów odroczenia w celu zoptymalizowania przebiegu układu.|
|**Renderowanie**|Czas spędzony na rysowaniu elementów XAML na ekranie.|
|**I/0**|Czas spędzony na pobierania danych z dysku lokalnego lub zasobów sieciowych, które są dostępne za pośrednictwem interfejsu API Microsoft [Windows Internet (WinINet).](/windows/desktop/WinInet/portal)|
|**Kod aplikacji**|Czas spędzony na wykonaniu kodu aplikacji (użytkownika), który nie jest związany z analizą ani układem.|
|**Xaml Inne**|Czas spędzony na wykonaniu kodu środowiska uruchomieniowego XAML.|

> [!TIP]
> Podczas uruchamiania **profilowania** wybierz narzędzie Użycie procesora CPU wraz **Oś czasu aplikacji,** aby wyświetlić metody aplikacji, które są wykonywane w wątku interfejsu użytkownika. Przeniesienie długotrwałego kodu aplikacji do wątku w tle może poprawić czas odpowiedzi interfejsu użytkownika.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a> Dostosowywanie szczegółów osi czasu

Użyj paska **narzędzi Szczegóły osi** czasu, aby sortować, filtrować i określać adnotacje wpisów widoku Szczegóły **osi** czasu.

|Nazwa|Opis|
|-|-|
|**Sortuj według**|Sortuj według czasu rozpoczęcia lub długości zdarzeń.|
|![Grupowanie zdarzeń według ramki](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Dodaje lub usuwa kategorię ramki najwyższego **poziomu,** która grupuje zdarzenia według ramki.|
|![Filtrowanie listy szczegółów osi czasu](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtruje listę według wybranych kategorii i długości zdarzeń.|
|![Dostosowywanie informacji o szczegółach osi czasu](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umożliwia określenie adnotacji do zdarzeń.|

## <a name="see-also"></a>Zobacz też

- [Blog zespołu WPF: Nowe narzędzie do analizy wydajności interfejsu użytkownika dla aplikacji WPF](/archive/blogs/wpf/new-ui-performance-analysis-tool-for-wpf-applications)
- [Najlepsze rozwiązania w zakresie wydajności dla aplikacji platformy UWP korzystających z języków C++, C# i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optymalizowanie wydajności aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)