---
title: Oś czasu aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f899e081377ecc1a56e141f8793d6f707df2b69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534085"
---
# <a name="application-timeline"></a>Oś czasu aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj profilera **oś czasu aplikacji** , aby znaleźć i rozwiązać problemy z wydajnością związane z interakcją aplikacji w aplikacjach XAML. To narzędzie ułatwia zwiększenie wydajności aplikacji XAML, zapewniając szczegółowy widok użycia zasobów aplikacji. Można analizować czas spędzony przez aplikację, przygotowując ramki interfejsu użytkownika (układ i renderowanie), obsługując żądania sieci i dysku, a także w scenariuszach takich jak uruchamianie aplikacji, ładowanie stron i zmiana rozmiaru systemu Windows.  
  
 **Oś czasu aplikacji** jest jednym z narzędzi, które można uruchomić za pomocą **profilera debugowania/wydajności.** ...  
  
 To narzędzie zastępuje narzędzie czasu **odpowiedzi interfejsu użytkownika XAML** , które było częścią zestawu narzędzi diagnostycznych dla Visual Studio 2013.  
  
 Tego narzędzia można użyć na następujących platformach:  
  
1. Aplikacje uniwersalne systemu Windows (w systemie Windows 10)  
  
2. Sklep Windows 8,1  
  
3. Windows Phone 8,1 (typowa platforma XAML)  
  
4. Windows Presentation Foundation (.NET 4,0 i nowsze)  
  
5. Windows 7  
  
> [!NOTE]
> Dane użycia procesora CPU i dane zużycia energii można zbierać i analizować wraz z danymi **ApplicationTimeline** . Zobacz [Uruchamianie narzędzi profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="collect-application-timeline-data"></a><a name="BKMK_Collect_Timeline_data_for_your_app"></a> Zbieranie danych Oś czasu aplikacji  
 Możesz profilować czas odpowiedzi aplikacji na komputerze lokalnym, podłączonym urządzeniu, symulatorze programu Visual Studio lub emulatorach lub urządzeniu zdalnym. Zobacz [Uruchamianie narzędzi profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
> [!TIP]
> Jeśli to możliwe, uruchom aplikację bezpośrednio na urządzeniu. Wydajność aplikacji zaobserwowanej w symulatorze lub za pomocą połączenia pulpitu zdalnego może nie być taka sama jak Rzeczywista wydajność na urządzeniu. Z drugiej strony zbieranie danych przy użyciu narzędzi zdalnych programu Visual Studio nie ma wpływu na dane wydajności.  
  
 Poniżej przedstawiono podstawowe kroki:  
  
1. Otwórz aplikację XAML.  
  
2. Kliknij pozycję **Debuguj/Performance Profiler..**.. W oknie. diagsession powinna zostać wyświetlona lista narzędzi profilowania.  
  
3. Wybierz **oś czasu aplikacji** a następnie kliknij przycisk **Rozpocznij** u dołu okna.  
  
    > [!NOTE]
    > Może zostać wyświetlone okno Kontrola konta użytkownika z prośbą o zgodę na uruchomienie VsEtwCollector.exe. Kliknij przycisk **Yes** (Tak).  
  
4. Uruchom scenariusz, który interesuje Cię w aplikacji, aby zbierać dane dotyczące wydajności.  
  
5. Aby zatrzymać profilowanie, przełącz się z powrotem do okna. diagsession, a następnie kliknij przycisk **Zatrzymaj** u góry okna.  
  
     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.  
  
     ![Raport profilera osi czasu](../profiling/media/timeline-base.png "TIMELINE_Base")  
  
## <a name="analyze-timeline-profiling-data"></a><a name="BKMK_Analyze_Timeline_profiling_data"></a> Analizowanie danych profilowania osi czasu  
 Po zebraniu danych profilowania można wykonać poniższe kroki, aby rozpocząć analizę:  
  
1. Zapoznaj się z informacjami w wykresach **użycia wątku interfejsu użytkownika** i **przepływności wizualizacji (FPS)** , a następnie użyj pasków nawigacyjnych osi czasu, aby wybrać zakres czasu, który chcesz analizować.  
  
2. Korzystając z informacji w wykresach **użycia wątku interfejsu użytkownika** lub **przepływności wizualizacji (FPS)** , sprawdź szczegóły w widoku **szczegóły osi czasu** , aby poznać możliwe przyczyny niewidocznego braku odpowiedzi.  
  
### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a> Scenariusze raportów, kategorie i zdarzenia  
 Narzędzie **oś czasu aplikacji** wyświetla dane chronometrażu dla scenariuszy, kategorii i zdarzeń, które są związane z wydajnością XAML.  
  
### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a> Oś czasu sesji diagnostycznej  
 ![Oś czasu wydajności i diagnostyki](../profiling/media/diaghub-timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Linijka w górnej części strony pokazuje oś czasu profilowanych informacji. Ta oś czasu ma zastosowanie do wykresu **wykorzystania wątków interfejsu użytkownika** i wykresu **przepływności wizualnej** . Można zawęzić zakres raportu, przeciągając paski nawigacyjne na osi czasu w celu zaznaczenia segmentu osi czasu.  
  
 Na osi czasu są także wyświetlane wstawione znaczniki użytkownika oraz zdarzenia cyklu życia aktywacji aplikacji.  
  
### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a> Wykres wykorzystania wątku interfejsu użytkownika  
 ![Wykres wykorzystania CPU](../profiling/media/timeline-cpuutilization.png "TIMELINE_CpuUtilization")  
  
 Wykres **wykorzystanie wątku interfejsu użytkownika (%)** to wykres słupkowy, który wyświetla względną ilość czasu spędzoną w kategorii dla zakresu kolekcji.  
  
### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a> Wykres przepływności wizualizacji (FPS)  
 ![Wykres przepływności wizualizacji](../profiling/media/timeline-visualthroughput.png "TIMELINE_VisualThroughput")  
  
 Wykres liniowy **przepływności (FPS)** pokazuje klatki na sekundę (FPS) w interfejsie użytkownika i wątku kompozycji dla aplikacji.  
  
### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a> Szczegóły osi czasu  
 Widok szczegółów to miejsce, w którym będziesz spędzać większość czasu na analizowanie raportu. Pokazuje szczegółowy widok użycia procesora CPU przez daną aplikację według podsystemu struktury interfejsu użytkownika lub składnika systemowego, który zużywał procesor CPU.  
  
 Obsługiwane są następujące zdarzenia:  
  
|Nazwa|Opis|  
|-|-|  
|**Asax**|Czas poświęcony na analizowanie plików XAML i tworzenie obiektów.<br /><br /> Rozwijanie węzła **analizy** w **szczegółach osi czasu** wyświetla łańcuch zależności wszystkich plików XAML, które zostały przeanalizowane w wyniku zdarzenia głównego. Umożliwi to zidentyfikowanie niepotrzebnych analiz plików i tworzenie obiektów w scenariuszach z uwzględnieniem wydajności i ich optymalizację.|  
|**Układ**|W dużych aplikacjach, tysiące elementów mogą być wyświetlane na ekranie w tym samym czasie. Może to spowodować niską szybkość klatek interfejsu użytkownika i odpowiadające im niewystarczająca czas odpowiedzi aplikacji. Zdarzenie układu dokładnie określa koszt zniesienia poszczególnych elementów (tj. czas poświęcony na rozmieszczenie, mierzenie, ApplyTemplate, ArrangeOverride i ArrangeOverride) i tworzy drzewa wizualne, które uczestniczyły w przejściu do układu. Możesz użyć tej wizualizacji, aby określić, które z drzew logicznych wymaga oczyszczenia, lub aby oszacować inne mechanizmy odroczenia, aby zoptymalizować przebieg układu.|  
|**Renderowanie**|Czas spędzony na rysowaniu elementów XAML na ekranie.|  
|**I/0**|Czas poświęcony na pobieranie danych z dysku lokalnego lub z zasobów sieciowych, do których dostęp odbywa się za pośrednictwem [interfejsu API Microsoft Windows Internet (WinInet)](https://msdn.microsoft.com/library/windows/desktop/aa385331.aspx).|  
|**Kod aplikacji**|Czas poświęcony na wykonywanie kodu aplikacji (użytkownika), który nie jest związany z analizowaniem ani układem.|  
|**Inne XAML**|Czas poświęcony na wykonanie kodu środowiska uruchomieniowego XAML.|  
  
> [!TIP]
> Wybierz narzędzie **użycie procesora CPU** wraz z **oś czasu aplikacji** narzędziem po rozpoczęciu profilowania, aby wyświetlić metody aplikacji wykonywane w wątku interfejsu użytkownika. Przeniesienie długotrwałego kodu aplikacji do wątku w tle może poprawić czas odpowiedzi interfejsu użytkownika.  
  
#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a> Dostosowywanie szczegółów osi czasu  
 Pasek narzędzi **szczegóły osi czasu** umożliwia sortowanie, filtrowanie i określanie adnotacji wpisów widoku **szczegółów osi czasu** .  
  
|Nazwa|Opis|  
|-|-|  
|**Sortuj według**|Sortuj według czasu rozpoczęcia lub długości zdarzeń.|  
|![Grupuj zdarzenia według ramki](../profiling/media/timeline-groupbyframes.png "TIMELINE_GroupByFrames")|Dodaje lub usuwa kategorię **ramek** najwyższego poziomu, która grupuje zdarzenia według ramki.|  
|![Filtruj listę szczegółów osi czasu](../profiling/media/timeline-filter.png "TIMELINE_Filter")|Filtruje listę według wybranych kategorii i długości zdarzeń.|  
|![Dostosuj informacje szczegółowe dotyczące osi czasu](../profiling/media/timeline-viewsettings.png "TIMELINE_ViewSettings")|Umożliwia określenie adnotacji do zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Blog zespołu WPF: nowe narzędzie do analizy wydajności interfejsu użytkownika dla aplikacji WPF](https://devblogs.microsoft.com/wpf/new-ui-performance-analysis-tool-for-wpf-applications/)   
 [Najlepsze rozwiązania w zakresie wydajności dla aplikacji ze sklepu Windows przy użyciu języków C++, C# i Visual Basic](https://msdn.microsoft.com/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [Optymalizacja wydajności aplikacji WPF](https://msdn.microsoft.com/library/ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf)
