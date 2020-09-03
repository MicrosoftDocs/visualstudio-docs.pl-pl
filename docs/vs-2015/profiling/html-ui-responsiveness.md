---
title: Czas odpowiedzi interfejsu użytkownika HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- performance, JavaScript [Windows Store apps]
- performance tools, JavaScript [Windows Store apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [Windows Store apps]
ms.assetid: da13070a-ba40-47dd-a846-ad72eed70d0b
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af2b71dd2169500b1c4a75ed59292779959d31a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299674"
---
# <a name="html-ui-responsiveness"></a>Czas odpowiedzi interfejsu użytkownika języka HTML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób izolowania problemów z wydajnością aplikacji przy użyciu profilera czas odpowiedzi interfejsu użytkownika, dostępnego dla uniwersalnych aplikacji systemu Windows.  
  
 Profiler czasu odpowiedzi interfejsu użytkownika może pomóc w izolowaniu problemów, takich jak problemy z czasem odpowiedzi interfejsu użytkownika lub wpływ na platformę, które zazwyczaj występują z następującymi objawami:  
  
- Brak odpowiedzi w interfejsie użytkownika. W przypadku zablokowania wątku interfejsu użytkownika aplikacja może działać powoli. Niektóre elementy, które mogą blokować wątek interfejsu użytkownika, obejmują nadmierny, synchroniczny kod JavaScript, nadmiarowy Układ CSS lub obliczenia CSS, synchroniczne żądania XHR, wyrzucanie elementów bezużytecznych, nadmierne malowanie lub kod JavaScript intensywnie korzystający z procesora.  
  
- Czas wolnego ładowania aplikacji lub strony. Jest to zazwyczaj spowodowane przez nadmierny czas ładowania zasobów.  
  
- Aktualizacje wizualne, które są mniej częste niż oczekiwano. Dzieje się tak, jeśli wątek interfejsu użytkownika jest zbyt zajęty, aby zachować gładką szybkość klatek. Na przykład jeśli wątek interfejsu użytkownika jest zajęty, ramki mogą zostać porzucone. Niektóre działania wątku innego niż interfejs użytkownika, takie jak żądania sieci, dekodowanie obrazu i farby, mogą również ograniczyć częstotliwość aktualizacji wizualnych. (Nie wszystkie elementy rysowania są wykonywane w wątku interfejsu użytkownika).  
  
## <a name="run-the-html-ui-responsiveness-tool"></a><a name="RunningProfiler"></a> Uruchamianie Narzędzia HTML czas odpowiedzi interfejsu użytkownika  
 Możesz użyć narzędzia do odpowiedzi interfejsu użytkownika HTML, gdy masz działającą aplikację systemu Windows w wersji uniwersalnej lub sklepu Windows, która jest otwarta w programie Visual Studio lub zainstalowana na komputerze z systemem Windows 8 lub nowszym.  
  
1. Jeśli używasz aplikacji z programu Visual Studio, na pasku narzędzi **Standardowy** na liście **Rozpocznij debugowanie** wybierz miejsce docelowe wdrożenia, takie jak jeden z emulatorów Windows Phone, **maszyna lokalna**, **symulator**lub **maszyna zdalna**.  
  
2. W menu **debugowanie** wybierz pozycję **Profiler wydajności.**...  
  
     Jeśli chcesz zmienić cel analizy profilera, wybierz pozycję**Zmień cel**.  
  
     ![Cel analizy zmian](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Dla celu analizy dostępne są następujące opcje:  
  
    - **Projekt startowy**. Wybierz tę opcję, aby przeanalizować bieżący projekt startowy. Jeśli aplikacja jest uruchamiana na komputerze zdalnym lub urządzeniu, należy użyć tego ustawienia, które jest wartością domyślną.  
  
    - **Uruchomiona aplikacja**. Wybierz tę opcję, aby wybrać aplikację ze sklepu Windows z listy uruchomionych aplikacji. Nie można użyć tej opcji, gdy aplikacja jest uruchamiana na komputerze zdalnym lub urządzeniu.  
  
         Za pomocą tej opcji można analizować wydajność aplikacji uruchomionych na komputerze, gdy nie masz dostępu do kodu źródłowego.  
  
    - **Zainstalowana aplikacja**. Wybierz tę opcję, aby wybrać zainstalowaną aplikację, którą chcesz przeanalizować. Nie można użyć tej opcji, gdy aplikacja jest uruchamiana na komputerze zdalnym lub urządzeniu.  
  
         Za pomocą tej opcji można analizować wydajność aplikacji zainstalowanych na komputerze, gdy nie masz dostępu do kodu źródłowego. Ta opcja może być również przydatna, gdy chcesz tylko analizować wydajność dowolnej aplikacji poza własnym programowaniem aplikacji.  
  
3. Z **dostępnych narzędzi**wybierz pozycję **czas odpowiedzi interfejsu użytkownika HTML**, a następnie wybierz polecenie **Uruchom**.  
  
4. Po uruchomieniu profilera czas odpowiedzi interfejsu użytkownika okno kontroli konta użytkowników może zażądać uprawnień do uruchamiania Collector.exe funkcji ETW programu Visual Studio. Wybierz opcję **tak**.  
  
     W celu przetestowania odpowiedniego scenariusza wydajności należy korzystać z aplikacji. Aby uzyskać szczegółowy przepływ pracy, zobacz [izolowanie problemu czasu odpowiedzi interfejsu użytkownika](#Workflow) i [izolowanie problemu dotyczącego przepływności wizualnej](#IsolateVisualThroughput).  
  
5. Przejdź do programu Visual Studio, naciskając klawisze Alt + Tab.  
  
6. Aby zatrzymać Profilowanie aplikacji i wyświetlić dane zebrane przez profiler, wybierz pozycję **Zatrzymaj zbieranie**.  
  
## <a name="isolate-an-issue"></a><a name="IsolateAnIssue"></a> Izolowanie problemu  
 Poniższa sekcja zawiera sugestie ułatwiające izolowanie problemów z wydajnością. Aby dowiedzieć się, jak identyfikować i rozwiązywać problemy z wydajnością za pomocą przykładowej aplikacji do testowania wydajności, zobacz [Przewodnik: poprawianie czasu odpowiedzi interfejsu użytkownika (html)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a> Izolowanie problemu dotyczącego czasu odpowiedzi interfejsu użytkownika  
 Te kroki zapewniają sugerowany przepływ pracy, który może pomóc w wydajniejszym użyciu profilera czas odpowiedzi interfejsu użytkownika:  
  
1. Otwórz aplikację w programie Visual Studio.  
  
2. Przetestuj aplikację pod kątem problemów z czasem odpowiedzi interfejsu użytkownika. (Naciśnij klawisze CTRL + F5, aby uruchomić aplikację bez debugowania).  
  
     Jeśli znajdziesz problem, Kontynuuj testowanie w celu zawężenia przedziału czasowego, w którym występuje problem, lub spróbuj zidentyfikować wyzwalacze, które powodują zachowanie.  
  
3. Przejdź do programu Visual Studio (naciśnij klawisze Alt + Tab) i Zatrzymaj aplikację (Shift + F5).  
  
4. Opcjonalnie możesz dodać znaczniki użytkownika do kodu przy użyciu [kodu znacznika do analizy](#ProfileMark).  
  
    > [!TIP]
    > Znaczniki użytkownika mogą ułatwić identyfikację problemu z czasem odpowiedzi podczas wyświetlania danych profilera. Na przykład można dodać znacznik użytkownika na początku i końcu sekcji kodu, która powoduje problem z czasem odpowiedzi.  
  
5. Uruchom Profiler czas odpowiedzi interfejsu użytkownika, postępując zgodnie z instrukcjami podanymi w poprzedniej sekcji.  
  
6. Umieść aplikację w stanie, który powoduje problem z czasem odpowiedzi interfejsu użytkownika.  
  
7. Przejdź do programu Visual Studio (naciśnij klawisze Alt + Tab) i wybierz pozycję **Zatrzymaj zbieranie** na karcie profilera profilera czas odpowiedzi interfejsu użytkownika.  
  
8. Jeśli dodano znaczniki użytkownika, pojawią się one w [widoku oś czasu sesji diagnostycznej](#Ruler) profilera. Na poniższej ilustracji przedstawiono pojedynczy znak użytkownika służący do określania konkretnej operacji w kodzie.  
  
     ![Linijka diagnostyki pokazująca znacznik użytkownika](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Określ obszar zainteresowania w osi czasu i grafy profilera przy użyciu znaczników użytkownika, zdarzeń cyklu życia aplikacji lub danych widocznych na wykresach. Poniżej przedstawiono niektóre wskazówki ułatwiające analizowanie i używanie danych na wykresach:  
  
    - Użyj [widoku oś czasu sesji diagnostycznej](#Ruler) , aby wyświetlić [kod znacznika dla analizy](#ProfileMark), zdarzenia cyklu życia aplikacji oraz skojarzoną oś czasu dla tych zdarzeń oraz oś czasu dla danych na innych wykresach.  
  
    - Wykres użycia [procesora CPU](#CPUUtilization) umożliwia wyświetlenie ogólnych informacji o aktywności procesora CPU i typie pracy, która jest obsługiwana w określonym przedziale czasu. Okresy nadmiernego działania procesora CPU są bardziej podobne do problemów z czasem reakcji i usuniętymi klatkami.  
  
    - W przypadku tworzenia gry lub zaawansowanej aplikacji multimedialnej Użyj [widoku przepływność wizualna (FPS)](#VisualThroughput) , aby zidentyfikować okresy, w których porzucana jest szybkość klatek.  
  
10. Wybierz obszar zainteresowania na jednym z grafów, klikając część wykresu i przeciągając wskaźnik, aby dokonać wyboru (lub za pomocą klawisza Tab i klawiszy strzałek). Po wybraniu przedziału czasu, w dolnym okienku programu profiler zostanie zmieniony wykres szczegóły osi czasu, aby wyświetlić tylko wybrany okres.  
  
     Na poniższej ilustracji przedstawiono wykres użycia procesora CPU z wyróżnionym obszarem zainteresowania.  
  
     ![Wykres użycia procesora CPU](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
11. [Szczegóły widoku osi czasu](#TimelineDetails) umożliwiają uzyskanie szczegółowych informacji o zdarzeniach, które są uruchamiane zbyt często lub przez zbyt dużo czasu. Na przykład poszukaj następujących:  
  
    - Detektory zdarzeń, czasomierze i wywołania zwrotne klatek animacji. W zależności od konkretnego zdarzenia podane dane mogą obejmować identyfikator zmodyfikowanych elementów DOM, nazwę zmodyfikowanych właściwości CSS, link do lokalizacji źródłowej oraz nazwę skojarzonego zdarzenia lub funkcji wywołania zwrotnego.  
  
    - Układ lub skrypty zdarzeń, które spowodowały renderowanie elementów, takich jak wywołania do `window.getComputedStyles` . Podano skojarzony element DOM dla zdarzenia.  
  
    - Strony lub zasoby adresów URL, które są ładowane przez aplikację, takie jak oceny skryptów dla zdarzeń analizy HTML. Podano nazwę pliku lub zasób.  
  
    - Inne zdarzenia określone w [Kompendium zdarzenia profilera](#ProfilerEvents).  
  
    > [!TIP]
    > Większość przydatnych informacji w profilerze pojawia się na wykresie szczegóły osi czasu.  
  
12. Po wybraniu obszaru na wykresie użycie procesora lub przepływność wizualna (FPS) wybierz pozycję **Powiększ** (menu kontekstowe), aby uzyskać bardziej szczegółowe informacje. Oś czasu dla wykresu zmieni się, aby pokazać tylko wybrany okres.  
  
13. W przypadku powiększania wybierz część wykresu użycia procesora lub wizualizacji przepływności. Po dokonaniu wyboru wykres szczegóły osi czasu w dolnym okienku profilera zostanie zmieniony, aby pokazać tylko wybrany okres.  
  
### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a> Izolowanie problemu dotyczącego przepływności wizualnej  
 Okresy nadmiernego użycia procesora CPU mogą spowodować niską lub niespójną szybkość klatek. Jeśli tworzysz rozbudowane aplikacje multimedialne i gry, wykres przepływności wizualnej może dostarczyć bardziej ważne dane niż wykres użycia procesora CPU.  
  
 Aby wyizolować problem dotyczący przepływności wizualnej, wykonaj kroki opisane w poprzedniej sekcji, ale Użyj grafu przepływności wizualnej jako jednego z najważniejszych punktów danych.  
  
### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a> Oznacz kod do analizy  
 Aby ułatwić odizolowanie sekcji kodu aplikacji, która jest skojarzona z danymi wyświetlanymi na wykresach, można dodać wywołanie funkcji w aplikacji, która instruuje Profiler, aby wstawiał znacznik użytkownika — odwrócony trójkąt — na osi czasu w momencie, gdy funkcja zostanie wykonana. Dowolny dodany znacznik użytkownika pojawia się na osi czasu wykresu użycia procesora CPU, wykresu przepływności wizualnej i wykresu szczegóły osi czasu.  
  
 Aby dodać znacznik użytkownika, Dodaj następujący kod do aplikacji. Ten przykład używa "pobierania danych" jako opisu zdarzenia.  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Opis zdarzenia jest wyświetlany jako etykietka narzędzia po umieszczeniu wskaźnika myszy nad oznaczeniem użytkownika. Możesz dodać dowolną liczbę znaków użytkownika.  
  
> [!NOTE]
> `console.timeStamp`, polecenie Chrome również pojawia się jako oznaczenie użytkownika.  
  
 Na poniższej ilustracji przedstawiono linijkę diagnostyki z pojedynczym znacznikiem użytkownika i jego etykietki narzędzia.  
  
 ![Linijka diagnostyki pokazująca znacznik użytkownika](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 Możesz również utworzyć zdarzenia generowane przez narzędzie w widoku Szczegóły osi czasu, aby pokazać czas, który przechodzi między dwoma znakami użytkownika. Poniższy kod dodaje drugi znacznik użytkownika i pomiar czasu, który przechodzi między wykonywaniem dwóch znaków użytkownika (poprzedni kod pokazuje pierwszy znacznik użytkownika).  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 Jeśli nie określono drugiego znacznika użytkownika, program `performance.measure` używa sygnatury czasowej jako drugiego znacznika użytkownika. Wymagany jest pierwszy znacznik użytkownika.  
  
 Pomiar czasu trwania pojawia się jako zdarzenie **miary użytkownika** w widoku szczegółów osi czasu i wyświetla szczegółowe informacje, gdy jest zaznaczone.  
  
 ![Zdarzenie miary użytkownika w widoku szczegółów osi czasu](../profiling/media/js-htmlvizprofiler-user-measure.png "JS_HTMLVizProfiler_User_Measure")  
  
## <a name="analyze-data"></a><a name="AnalyzeData"></a> Analizowanie danych  
 W poniższych sekcjach znajdują się informacje ułatwiające interpretowanie danych w programie Profiler.  
  
### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a> Wyświetlanie osi czasu sesji diagnostycznej  
 Linijka u góry profilera pokazuje oś czasu dla profilowanych informacji. Ta oś czasu ma zastosowanie do wykresu użycia procesora CPU i wykresu przepływności wizualnej.  
  
 Oto jak wygląda oś czasu sesji diagnostycznej z etykietą narzędzia wyświetlaną dla kilku zdarzeń cyklu życia aplikacji:  
  
 ![Linijka sesji diagnostycznej](../profiling/media/js-htmlvizprof-ruler.png "JS_HTMLVizProf_Ruler")  
  
 Oś czasu pokazuje, kiedy wystąpią zdarzenia lifecyle aplikacji, takie jak zdarzenie aktywacji, i wyświetla znaczniki użytkownika (Trójkąty oznaczania użytkownika), które można dodać do kodu. Możesz wybrać zdarzenia, aby wyświetlić etykietki narzędzi zawierające więcej informacji. Aby uzyskać więcej informacji na temat znaczników użytkownika, zobacz [Mark Code for Analysis](#ProfileMark) w tym temacie.  
  
 Zdarzenia cyklu życia aplikacji są wyświetlane jako symbole diamentów. Są to zdarzenia modelu DOM, które obejmują następujące elementy:  
  
- `DOMContentLoaded` i `Load` zdarzenia, które zazwyczaj występują w programie obsługi zdarzeń aktywowanych w kodzie. Etykietka narzędzia dla zdarzenia zawiera określone zdarzenie i adres URL.  
  
- Zdarzenie nawigacji, które występuje po przejściu do innej strony. Etykietka narzędzia dla zdarzenia zawiera adres URL strony docelowej.  
  
### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a> Wyświetl użycie procesora CPU  
 Wykres użycia procesora CPU umożliwia zidentyfikowanie okresów czasu, w którym występuje zbyt duże działanie procesora CPU. Zawiera informacje na temat średniego użycia procesora przez aplikację w danym okresie czasu. Informacje są kodowane kolorami, aby reprezentować następujące kategorie: **ładowanie**, **wykonywanie skryptów**, odzyskiwanie pamięci (**GC**), **Style**, **renderowanie**i **Dekodowanie obrazu**. Więcej informacji o tych kategoriach znajduje się w sekcji [Informacje o zdarzeniu profilera](#ProfilerEvents) w dalszej części tego tematu.  
  
 Wykres użycia procesora CPU przedstawia ilość czasu poświęcanego na wszystkie wątki aplikacji, łącząc wartości użycia procesora CPU dla jednego lub większej liczby procesorów CPU w jedną wartość procentową. Wartość użycia procesora CPU może przekroczyć 100 procent, gdy jest używany więcej niż jeden procesor CPU.  
  
> [!NOTE]
> Użycie procesora GPU nie pojawia się na wykresie.  
  
 Ten przykład pokazuje, jak wygląda wykres użycia procesora CPU:  
  
 ![Wykres użycia procesora CPU](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
 Użyj tego wykresu, aby:  
  
- Zidentyfikuj ogólne obszary problemu.  
  
- Wybierz określony przedział czasu, który ma być wyświetlany na wykresie szczegółów osi czasu. Aby wybrać okres, zaznacz część wykresu i przeciągnij wskaźnik, aby dokonać wyboru.  
  
- Uzyskaj bardziej szczegółowy widok wybranego przedziału czasu, wybierając przycisk **Powiększ** .  
  
  Aby uzyskać więcej informacji na temat korzystania z grafu, zobacz [izolowanie problemu czasu odpowiedzi interfejsu użytkownika](#Workflow) w tym temacie.  
  
### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a> Wyświetl przepływność wizualną (FPS)  
 Wykres przepływności wizualnej pozwala identyfikować okresy, w których porzucana jest szybkość klatek. Pokazuje on klatki na sekundę (FPS) dla aplikacji. Ten Graf jest najbardziej przydatny do tworzenia gier i bogatych aplikacji multimedialnych.  
  
 Wartość wyświetlonej FPS może się różnić od rzeczywistej szybkości klatek. Podczas badania danych w tym grafie należy pamiętać o następujących kwestiach:  
  
- Wykres pokazuje, że aplikacja jest w stanie osiągnąć w określonym czasie. Gdy aplikacja jest bezczynna, liczba klatek na sekundę jest taka sama jak częstotliwość odświeżania monitora.  
  
- Wykres pokazuje rzeczywistą wartość FPS, jeśli aplikacja wykonuje działania, które wymagają aktualizacji wizualnych.  
  
- Wykres pokazuje wartość zero, jeśli ramki są usuwane.  
  
  Ten przykład pokazuje, jak wygląda wykres przepływności wizualnej:  
  
  ![Wykres przepływności wizualizacji](../profiling/media/js-htmlvizprof-vizthru.png "JS_HTMLVizProf_VizThru")  
  
  Użyj grafu przepływności wizualnej, aby:  
  
- Zidentyfikuj ogólne obszary problemu.  
  
- Wybierz określony przedział czasu, który ma być wyświetlany na wykresie szczegółów osi czasu. Aby wybrać okres, zaznacz część wykresu i przeciągnij wskaźnik, aby dokonać wyboru.  
  
- Uzyskaj bardziej szczegółowy widok wybranego przedziału czasu, wybierając przycisk **Powiększ** .  
  
### <a name="view-timeline-details"></a><a name="TimelineDetails"></a> Wyświetl szczegóły osi czasu  
 Wykres szczegóły osi czasu jest wyświetlany w dolnym okienku profilera czas odpowiedzi interfejsu użytkownika. Zawiera sekwencyjne i hierarchiczne informacje o zdarzeniach, które zużywają najwięcej czasu procesora CPU w wybranych okresach. Ten Graf może pomóc w ustaleniu, co wyzwoliło konkretne zdarzenie, a także w przypadku niektórych zdarzeń, jak mapowanie zdarzeń z powrotem do kodu źródłowego. Ten wykres pomaga również określić czas wymagany do malowania aktualizacji wizualnych na ekranie.  
  
 Na wykresie przedstawiono pracę wątku interfejsu użytkownika i pracujesz nad wątkami w tle, które mogą współtworzyć w celu powolnej aktualizacji wizualnej Wykres nie pokazuje pracy JIT języka JavaScript, asynchronicznej pracy procesora GPU, pracy wykonanej poza procesem hosta (na przykład RuntimeBroker.exe i dwm.exe pracy) lub pracy dla obszarów środowisko wykonawcze systemu Windows, które nie zostały jeszcze instrumentacji do profilowania (na przykład we/wy dysku).  
  
> [!TIP]
> Gdy zdarzenie wystąpi w wątku w tle, identyfikator wątku pojawia się w nawiasach obok nazwy zdarzenia.  
  
 Ten przykład pokazuje, jak wygląda wykres szczegółów osi czasu, gdy zaznaczono odbiornik zdarzeń dla zdarzenia kliknięcia modelu DOM:  
  
 ![Wykres szczegółów osi czasu](../profiling/media/js-htmlvizprof-timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Na tej ilustracji program obsługi zdarzeń **spinAction** w kolumnie **Nazwa zdarzenia** jest łączem, które po zaznaczeniu spowoduje przejście do programu obsługi zdarzeń w kodzie źródłowym. W okienku po prawej stronie Właściwość **funkcji wywołania zwrotnego** zapewnia ten sam link do kodu źródłowego. Inne właściwości zawierają również informacje dotyczące zdarzenia, takie jak skojarzony element DOM.  
  
 W przypadku wybrania części osi czasu dla wykresu użycie procesora i przepływność wizualna (FPS) wykres szczegóły osi czasu pokazuje szczegółowe informacje o wybranym okresie.  
  
 Zdarzenia na wykresie szczegóły osi czasu są kodowane kolorami, aby reprezentować te same kategorie pracy, które są wyświetlane na wykresie użycia procesora CPU. Aby uzyskać więcej informacji na temat kategorii zdarzeń i określonych zdarzeń, zobacz temat [Informacje o zdarzeniu profilera](#ProfilerEvents) w tym temacie.  
  
 Użyj wykresu szczegóły osi czasu, aby:  
  
- Wyświetl przybliżony czas rozpoczęcia, czas trwania i czasy zakończenia dla zdarzenia w widoku osi czasu i siatki. Wykres szczegóły osi czasu może zawierać okresy od 30 milisekund do 30 sekund w widoku siatki, w zależności od stanu powiększenia. Dla wartości czasu trwania:  
  
  - Czas włączny reprezentuje czas trwania zdarzenia, łącznie z elementami podrzędnymi zdarzeń. W widoku siatki ta wartość jest wyświetlana jako pierwsza.  

  - Czas wyłączny reprezentuje czas trwania zdarzenia, bez uwzględniania elementów podrzędnych zdarzenia. W widoku siatki ta wartość jest wyświetlana w nawiasach.  
  
- Rozwiń zdarzenie w hierarchii, aby wyświetlić elementy podrzędne zdarzenia. Zdarzenia podrzędne są inne zdarzenia, które są wywoływane przez zdarzenie nadrzędne. Na przykład zdarzenie DOM może mieć detektory zdarzeń, które są wyświetlane jako elementy podrzędne. Odbiornik zdarzeń może mieć inne zdarzenia, które wynikają z tego, takie jak zdarzenie układu.  
  
- Sortuj zdarzenia według czasu rozpoczęcia (wartość domyślna) lub czas trwania. Użyj listy **Sortuj według** , aby wybrać metodę sortowania.  
  
- Wyświetl szczegóły każdego zdarzenia w okienku szczegółów (okienko po prawej stronie). Właściwości różnią się w zależności od konkretnego zdarzenia, jak pokazano w tych przykładach:  
  
  - W przypadku czasomierzy, detektorów zdarzeń (zdarzeń DOM) i wywołań zwrotnych ramki animacji Właściwość **funkcji wywołania zwrotnego** zawiera link do lokalizacji kodu źródłowego wraz z nazwą procedury obsługi zdarzeń lub funkcji wywołania zwrotnego.  

  - W przypadku czasomierzy, detektorów zdarzeń (zdarzeń DOM), zdarzeń układu i wywołań zwrotnych ramki animacji, podsumowanie oznaczone kolorem dla wybranego zdarzenia i wszystkie jego elementy podrzędne są wyświetlane w sekcji **Podsumowanie łącznego czasu** (pierścień kodowany kolorem). Każdy wycinek oznaczony kolorem obrazu reprezentuje typ zdarzenia. Etykietki narzędzi zawierają nazwę typu zdarzenia.  

  > [!TIP]
  > Wykres szczegółów osi czasu i **Podsumowanie łącznego czasu** mogą pomóc identyfikować obszary na potrzeby optymalizacji. Jeśli jeden z tych widoków zawiera dużą liczbę małych zadań, zdarzenie może być kandydatem do optymalizacji. Na przykład aplikacja może odświeżać elementy DOM często, co powoduje dużą liczbę zdarzeń dotyczących układu i kodu HTML. Może być możliwe zoptymalizowanie wydajności przez przetwarzanie wsadowe tej pracy.  

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a> Szczegóły filtru osi czasu  
 Możesz filtrować widok w szczegółach osi czasu do określonego zdarzenia, wybierając pozycję **Filtruj do zdarzenia** z menu kontekstowego dla określonego zdarzenia. Po wybraniu tej opcji, oś czasu i widok siatki są objęte zakresem wybranego zdarzenia. Wybór na wykresie użycia procesora CPU także zakresy do określonego zdarzenia.  
  
 ![Filtrowanie osi czasu do zdarzenia](../profiling/media/js-htmlvizprofiler-filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
### <a name="filter-events"></a><a name="FilterEvents"></a> Filtruj zdarzenia  
 Możesz odfiltrować niektóre zdarzenia z wykresu szczegółów osi czasu, aby zmniejszyć szum w danych lub wyeliminować dane, które nie są interesujące dla scenariusza wydajności. Można filtrować według nazwy zdarzenia lub czasu trwania zdarzenia lub według określonych filtrów opisanych tutaj.  
  
 Aby odfiltrować Dekodowanie obrazu, pobieranie spekulacyjne i zdarzenia GC, wyczyść opcję **działania w tle** z ikony filtru w dolnym okienku. Ponieważ te zdarzenia nie są bardzo funkcjonalne, są domyślnie ukryte.  
  
 ![Filtrowanie zdarzeń na osi czasu](../profiling/media/js-htmlvizprofiler-event-filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 Aby odfiltrować zdarzenia żądań HTTP, usuń zaznaczenie opcji **ruch sieciowy** z ikony filtru w dolnym okienku. Domyślnie te zdarzenia są wyświetlane na wykresie szczegóły osi czasu.  
  
 Aby odfiltrować działanie wątku interfejsu użytkownika, wyczyść opcję **działania interfejsu użytkownika** .  
  
> [!TIP]
> Usuń zaznaczenie tej opcji i wybierz opcję ruchu sieciowego, aby zbadać problemy związane z opóźnieniem sieci.  
  
 Aby odfiltrować miary użytkownika, wyczyść opcję **miary użytkownika** . Miary użytkownika to zdarzenia najwyższego poziomu bez elementów podrzędnych.  
  
### <a name="group-events-by-frame"></a><a name="GroupFrames"></a> Grupuj zdarzenia według ramki  
 Zdarzenia, które są wyświetlane w widoku szczegółów osi czasu, można zgrupować do poszczególnych ramek. Te zdarzenia klatek to zdarzenia generowane przez narzędzie i reprezentujące kontenery zdarzeń najwyższego poziomu dla wszystkich zadań związanych z wątkiem interfejsu użytkownika, które występują między zdarzeniami programu Paint. Aby włączyć ten widok, wybierz pozycję **Grupuj zdarzenia najwyższego poziomu według ramek**.  
  
 ![Grupuj zdarzenia najwyższego poziomu według ramki](../profiling/media/js-htmlvizprofiler-frame-grouping-button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Gdy grupujesz zdarzenia według ramki, zdarzenia najwyższego poziomu w widoku Szczegóły osi czasu reprezentują ramkę.  
  
 ![Zdarzenia osi czasu pogrupowane według ramki](../profiling/media/js-htmlvizprofiler-frame-grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
## <a name="save-a-diagnostic-session"></a><a name="SaveSession"></a> Zapisywanie sesji diagnostycznej  
 W programie Visual Studio można zapisać sesję diagnostyczną, gdy zamkniesz kartę, która jest skojarzona z sesją. Zapisane sesje można otworzyć ponownie w późniejszym czasie.  
  
## <a name="profiler-event-reference"></a><a name="ProfilerEvents"></a> Dokumentacja zdarzenia profilera  
 Zdarzenia profilera są podzielone na kategorie i kodowane kolorem w profilerze czas odpowiedzi interfejsu użytkownika. Są to kategorie zdarzeń:  
  
- **Ładowaniu.** Wskazuje czas poświęcony na pobieranie zasobów aplikacji oraz analizowanie kodu HTML i CSS podczas pierwszego ładowania aplikacji. Może to obejmować żądania sieciowe.  
  
- **Wykonywania.** Wskazuje czas spędzony na analizie i uruchamianiu języka JavaScript. Obejmuje to zdarzenia DOM, czasomierze, ocenę skryptu i działanie ramki animacji. Obejmuje zarówno kod użytkownika, jak i kod biblioteki.  
  
- **Globalnego.** Wskazuje czas spędzony na wyrzucaniu elementów bezużytecznych.  
  
- **Stylów.** Wskazuje czas spędzony na analizie CSS i obliczaniu prezentacji i układu elementu.  
  
- **Dawania.** Wskazuje czas spędzony na malowaniu ekranu.  
  
- **Dekodowanie obrazu.** Wskazuje czas poświęcony na dekompresowanie i dekodowanie obrazów.  
  
  W przypadku kategorii skryptu i stylu Profiler czas odpowiedzi interfejsu użytkownika może dostarczać dane, na których można wykonywać działania na wykresie szczegóły osi czasu. W przypadku zidentyfikowania problemów z obsługą skryptów jako problemu można uruchomić Profiler próbkowania procesora z profilerem czasu odpowiedzi interfejsu użytkownika. Alternatywnie możesz użyć profilera funkcji programu Visual Studio, aby uzyskać bardziej szczegółowe dane. Aby uzyskać więcej informacji, zobacz [Analizowanie danych chronometrażu funkcji JavaScript](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b).  
  
  W przypadku innych kategorii zdarzeń może być możliwe zidentyfikowanie efektów ubocznych platformy, które powodują dodanie funkcji do aplikacji, ale w takich przypadkach może nie być możliwe rozwiązanie konkretnych problemów z wydajnością przy użyciu profilera czas odpowiedzi interfejsu użytkownika.  
  
  W tej tabeli przedstawiono zdarzenia i ich opisy:  
  
|Wydarzenie|Kategoria zdarzenia|Występuje, gdy|  
|-----------|--------------------|-----------------|  
|Analizowanie kodu CSS|Ładowaniu|Napotkano nową zawartość CSS i podjęto próbę przeanalizowania zawartości CSS.|  
|Analiza kodu HTML|Ładowaniu|Napotkano nową zawartość HTML i podjęto próbę przeanalizowania zawartości w węzłach i wstawienia zawartości do drzewa modelu DOM.|  
|Żądanie HTTP|Ładowaniu|Znaleziono zasób zdalny w modelu DOM lub utworzono element XMLHttpRequest, który spowodowało żądanie HTTP.|  
|Pobieranie spekulacyjne|Ładowaniu|Zawartość HTML strony przeszukał wymagane zasoby, aby kolejne żądania HTTP dotyczące zasobów mogły być zaplanowane szybko.|  
|Funkcja wywołania zwrotnego ramki animacji|Obsługa skryptów|Przeglądarka przerenderuje kolejną ramkę i wywołała funkcję wywołania zwrotnego podaną przez aplikację.|  
|Wydarzenie DOM|Obsługa skryptów|Wystąpiło zdarzenie DOM i zostało wykonane.<br /><br /> `context`Właściwość dla zdarzenia dom, taka jak `DOMContentLoaded` lub `click` , jest pokazywana w nawiasach.|  
|Odbiornik zdarzeń|Obsługa skryptów|Odbiornik zdarzeń został wywołany i wykonany.|  
|Odbiornik zapytań o multimedia|Obsługa skryptów|Zarejestrowane zapytanie o multimedia zostało unieważnione, co spowodowało wykonanie skojarzonych z nim odbiorników.|  
|Obserwator mutacji|Obsługa skryptów|Co najmniej jeden z obserwowanych elementów DOM został zmodyfikowany, co spowodowało wykonanie wywołania zwrotnego skojarzonego z MutationObserver.|  
|Obliczanie skryptu|Obsługa skryptów|W modelu DOM znaleziono nowy element skryptu i podjęto próbę przeanalizowania i wykonania skryptu.|  
|Czasomierz|Obsługa skryptów|Upłynął zaplanowany czasomierz, który spowodował wykonanie skojarzonej funkcji wywołania zwrotnego.|  
|środowisko wykonawcze systemu Windows asynchronicznej funkcji wywołania zwrotnego|Obsługa skryptów|Operacja asynchroniczna, która wyzwoliła `Promise` funkcję wywołania zwrotnego została wykonana przez obiekt środowisko wykonawcze systemu Windows.|  
|Zdarzenie środowisko wykonawcze systemu Windows|Obsługa skryptów|Zdarzenie, które wystąpiło w obiekcie środowisko wykonawcze systemu Windows wyzwolił zarejestrowany odbiornik.|  
|Wyrzucanie elementów bezużytecznych|GC|Czas poświęcony na zbieranie pamięci dla obiektów, które nie były już używane.|  
|Obliczenia CSS|Style|Wprowadzono zmiany w modelu DOM, które wymagały ponownego obliczenia właściwości stylu wszystkich elementów, których dotyczy.|  
|Layout|Style|Wprowadzono zmiany w modelu DOM, które wymagały ponownego obliczenia rozmiaru i/lub pozycji wszystkich elementów, których dotyczy.|  
|Obrazu|Renderowanie|Wprowadzono zmiany wizualne w modelu DOM i podjęto próbę ponownego renderowania części strony.|  
|Warstwa renderowania|Renderowanie|Wprowadzono zmiany wizualne do niezależnie renderowanego fragmentu modelu DOM (zwanego warstwą) i zmiany wymagały renderowania części strony.|  
|Dekodowanie obrazu|Dekodowanie obrazu|Obraz został dołączony do modelu DOM i podjęto próbę dekompresowania i zdekodowania obrazu z oryginalnego formatu do mapy bitowej.|  
|Klatka|Brak|Wprowadzono zmiany wizualne w modelu DOM, które wymagały narysowania wszystkich części strony, których dotyczą. Jest to zdarzenie generowane przez narzędzie używane do grupowania.|  
|Miara użytkownika|Brak|Scenariusz specyficzny dla aplikacji został zmierzony przy użyciu `performance.measure` metody. Jest to zdarzenie generowane przez narzędzie służące do analizowania kodu.|  
  
## <a name="additional-information"></a><a name="Tips"></a> Dodatkowe informacje  
  
- Obejrzyj [ten film wideo](https://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Build 2013 dotyczącej profilera czas odpowiedzi interfejsu użytkownika.  
  
- Przeczytaj porady dotyczące wydajności aplikacji ze sklepu Windows dla systemu Windows za pomocą języka JavaScript. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania w zakresie wydajności dla aplikacji do sklepu Windows przy użyciu języka JavaScript](https://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
- Aby uzyskać informacje na temat modelu wykonywania jednowątkowego i wydajności, zobacz [wykonywanie kodu](https://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności aplikacji](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)
