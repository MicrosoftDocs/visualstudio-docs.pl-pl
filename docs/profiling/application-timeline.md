---
title: Analizowanie zużycia zasobów w aplikacjach XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 32368b280faf7b87aa128865cf169c7675a58c95
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059181"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analizowanie zużycia zasobów i aktywności wątku interfejsu użytkownika (XAML)

Użyj **oś czasu aplikacji** profiler, aby znaleźć i naprawić interakcji aplikacji dotyczące problemów z wydajnością w aplikacjach XAML. To narzędzie pozwala zwiększyć wydajność aplikacji XAML, pokazując szczegółowy widok wykorzystania zasobów aplikacji. Możesz analizować czas spędzony przez aplikację na przygotowanie ramek interfejsu użytkownika (układ i renderowania), obsługi żądań dysku i sieci oraz w scenariuszach, takich jak uruchamianie aplikacji i ładowanie strony i rozmiar Windows.

**Oś czasu aplikacji** jest jednym z narzędzi, można uruchomić z **debugowania** > **Profiler wydajności** polecenia.

To narzędzie zastępuje **XAML UI Responsiveness** narzędzie, które było częścią zestawu narzędzi diagnostycznych dla programu Visual Studio 2013.

To narzędzie służy na następujących platformach:

- Windows Universal apps (w systemie Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 i nowsze)
- Windows 7

> [!NOTE]
> Można zbierać i analizować dane użycia procesora CPU i dane zużycia energii, wraz z **ApplicationTimeline** danych. Zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
## <a name="collect-application-timeline-data"></a>Zbieranie danych oś czasu aplikacji

Czas reakcji aplikacji można profilować na komputerze lokalnym, podłączone urządzenie, symulatorze programu Visual Studio lub emulatorach lub urządzenie zdalne. Zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Jeśli to możliwe Uruchom aplikację bezpośrednio na urządzeniu. Wydajność aplikacji obserwowana na symulatorze lub za pośrednictwem połączenia pulpitu zdalnego może nie być taka sama jak rzeczywista wydajność na urządzeniu. Z drugiej strony zbieranie danych przy użyciu narzędzia zdalne programu Visual Studio nie ma wpływu na dane wydajności.  

Poniżej przedstawiono podstawowe kroki:  

1. Otwórz aplikację XAML.

2. Kliknij przycisk **debugowanie / Profiler wydajności**. Powinien zostać wyświetlony listę narzędzi w oknie .diagsession profilowania.

3. Wybierz **oś czasu aplikacji** a następnie kliknij przycisk **Start** w dolnej części okna.

   > [!NOTE]
   > Może widzieć okno Kontrola konta użytkownika żądaniem udzielenia uprawnienia do uruchamiania *VsEtwCollector.exe*. Kliknij przycisk **Tak**.

4. Uruchom scenariuszu jesteś zainteresowany profilowania w aplikacji, aby zbierać dane dotyczące wydajności.

5. Aby zatrzymać profilowanie, Przełącz do okna .diagsession, a następnie kliknij przycisk **zatrzymać** w górnej części okna.

   Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

   ![Raport programu profilującego osi czasu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analizowanie danych profilowania osi czasu

Po zebraniu danych profilowania można wykonać poniższe kroki, aby rozpocząć analizę:  
  
1. Przejrzyj informacje na **wykorzystanie wątku interfejsu użytkownika** i **przepustowość wizualna (kl. / s)** wykresów, a następnie użyj pasków nawigacyjnych osi czasu, aby wybrać zakres czasu do przeanalizowania.  
  
2. Korzystając z informacji podanych w **wykorzystanie wątku interfejsu użytkownika** lub **przepustowość wizualna (kl. / s)** wykresy, sprawdź szczegóły w **szczegóły osi czasu** widok, aby znaleźć możliwe przyczyny Brak seeming czas odpowiedzi.
  
### <a name="BKMK_Report_scenarios_categories_and_events"></a> Scenariusze, kategorii lub zdarzeń  

**Oś czasu aplikacji** narzędzie wyświetli dane chronometrażu dla scenariuszy, kategorie i zdarzenia, które są związane z wydajnością XAML.  

### <a name="BKMK_Diagnostic_session_timeline"></a> Oś czasu sesji diagnostycznej  

![Oś czasu wydajności i diagnostyki](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  

Linijka u góry strony pokazuje oś czasu dla profilowanych informacji. Ta oś czasu ma zastosowanie do obu **wykorzystanie wątku interfejsu użytkownika** wykresu i **przepustowość wizualna** wykresu. Można zawęzić zakres raportu, przeciągając paski nawigacyjne na osi czasu w celu zaznaczenia segmentu osi czasu.  

Oś czasu są również wyświetlane wstawione znaczniki użytkownika oraz zdarzenia cyklu życia aktywacji aplikacji.  

### <a name="BKMK_UI_thread_utilization_graph"></a> Wykres wykorzystania wątku interfejsu użytkownika

![Wykres wykorzystania procesora CPU](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  

**Wykorzystanie wątku interfejsu użytkownika (%)** wykresu jest wykres słupkowy, który wyświetla względna ilość czasu spędzonego w kategorii, aby w przedziale kolekcji.  

### <a name="BKMK_Visual_throughput_FPS_graph"></a> Wykres przepustowość wizualna (kl. / s)  

![Wykres przepustowość wizualna](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  

**Przepustowość wizualna (kl. / s)** wykres liniowy pokazuje liczbę klatek na sekundę (kl. / s) w wątku interfejsu użytkownika i kompozycję aplikacji.  

### <a name="BKMK_Timeline_details_"></a> Szczegóły osi czasu  

Widok szczegółów jest spędzisz tutaj większość czasu analizowanie raportu. Prezentuje sposób użycia procesora CPU przez aplikację, pogrupowane według podsystemu struktury interfejsu użytkownika lub składnik systemu, który procesor CPU wykorzystany.

Obsługiwane są następujące zdarzenia:  

|||  
|-|-|  
|**Analiza kodu**|Czas poświęcony na podczas analizowania plików XAML i tworzenia obiektów.<br /><br /> Rozwijanie **analizowanie** w węźle **szczegóły osi czasu** Wyświetla łańcuch zależności wszystkie pliki XAML, które były analizowane z powodu zdarzenia katalogu głównego. Tej porady pozwala zidentyfikować niepotrzebnego pliku podczas analizowania i obiektu tworzenia w scenariuszach poufnych wydajności i zoptymalizować je automatycznie.|  
|**Układ**|W przypadku dużych aplikacji tysięcy elementów mogą być wyświetlane na ekranie, w tym samym czasie. Ten ekran może prowadzić do niskiej szybkości klatek interfejsu użytkownika i czas odpowiedzi aplikacji odpowiednio niska. Zdarzenie układu określają dokładnie koszt układania każdego elementu (oznacza to, że czas spędzony w rozmieszczanie, miary, ApplyTemplate, ArrangeOverride i MeasureOverride). Ale sprzyja wytwarzaniu drzew wizualne, które uczestniczyła w przekazanie układu. Aby określić, które drzewa logiczne, aby oczyścić lub w celu oceny innych mechanizmów opóźnienia, aby zoptymalizować układ subskrypcji — okres próbny, można użyć tej wizualizacji.|  
|**Renderowanie**|Czas poświęcony na rysunku elementów XAML do ekranu.|  
|**I/0**|Czas poświęcony na pobieranie danych z dysku lokalnego lub z zasobów sieciowych, które są dostępne za pośrednictwem [Microsoft Windows Internet (WinINet) interfejsu API](/windows/desktop/WinInet/portal).|  
|**Kod aplikacji**|Czas poświęcony na wykonywanie kodu aplikacji (użytkownik), które nie są związane z analizą składni ani układu.|  
|**XAML — inne**|Czas poświęcony na wykonywanie kodu czasu wykonywania XAML.|  
  
> [!TIP]
> Wybierz **użycie procesora CPU** narzędzia wraz z **oś czasu aplikacji** narzędzia w przypadku uruchamiania profilowania na przeglądanie aplikacji metod, które są wykonywane w wątku interfejsu użytkownika. Przenoszenie kodu aplikacji długotrwałych do wątku w tle może poprawić czas odpowiedzi interfejsu użytkownika.  
  
#### <a name="BKMK_Customizing_Timeline_details_"></a> Dostosowywanie szczegóły osi czasu  

Użyj **szczegóły osi czasu** narzędzi, aby sortowanie, filtrowanie i podaj adnotacje **szczegóły osi czasu** zapisy.  
  
|||  
|-|-|  
|**Sortuj według**|Sortuj według czasu rozpoczęcia lub długość zdarzenia.|  
|![Grupuj zdarzenia według ramki](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Dodaje lub usuwa najwyższego poziomu **ramki** kategorię, która grupuje zdarzenia przez ramkę.|  
|![Lista szczegółów osi czasu filtrów](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtruje listę według wybranych kategorii i długość zdarzenia.|  
|![Dostosowywanie osi czasu szczegółowe informacje o](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umożliwia określenie adnotacje do zdarzenia.|  
  
## <a name="see-also"></a>Zobacz także

- [Blog zespołu programu WPF: nowy interfejs użytkownika narzędzia do analizy wydajności dla aplikacji WPF](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)  
- [Wydajność — najlepsze rozwiązania dla aplikacji platformy uniwersalnej systemu Windows przy użyciu języka C++, C# i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optymalizowanie wydajności aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
- [Profilowanie w programie Visual Studio](../profiling/index.md)  
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
