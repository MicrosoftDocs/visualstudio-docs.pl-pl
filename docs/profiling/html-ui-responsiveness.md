---
title: Analizowanie reakcji interfejsu użytkownika HTML w aplikacjach platformy uniwersalnej systemu Windows | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- performance, JavaScript [UWP apps]
- performance tools, JavaScript [UWP apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: a483d1382ea1f67c14aa4674016331bfe0f76e7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189370"
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>Analizowanie responsywności interfejsu użytkownika HTML w uniwersalnych aplikacjach systemu Windows
W tym temacie opisano sposób izolowania problemów z wydajnością w aplikacjach przy użyciu profilera czas reakcji interfejsu użytkownika, narzędzia wydajności dostępnego dla uniwersalnych aplikacji systemu Windows.

 Profiler responsywności interfejsu użytkownika może pomóc wyizolowaniu problemów, takich jak problemy z odpowiedzią interfejsu użytkownika lub skutki uboczne platformy, które zwykle występują z tymi objawami:

- Brak reakcji w interfejsie użytkownika. Aplikacja może być powolny, aby odpowiedzieć, jeśli wątek interfejsu użytkownika jest coraz zablokowane. Niektóre rzeczy, które mogą blokować wątek interfejsu użytkownika obejmują nadmierny synchroniczne kodu JavaScript, nadmierne układu CSS lub pracy obliczeniowej CSS, synchroniczne żądania XHR, wyrzucanie elementów bezużytecznych, nadmierne czasy malowania lub procesoro intensywne kodu JavaScript.

- Powolny czas ładowania aplikacji lub strony. Jest to zazwyczaj spowodowane przez nadmierny czas spędzony na ładowanie zasobów.

- Aktualizacje wizualne, które są rzadsze niż oczekiwano. Dzieje się tak, jeśli wątek interfejsu użytkownika jest zbyt zajęty, aby zachować płynną liczbę klatek na sekundę. Na przykład jeśli wątek interfejsu użytkownika jest zajęty, ramki mogą zostać usunięte. Niektóre prace wątku innych niż interfejs użytkownika, takie jak żądania sieciowe, dekodowanie obrazu i farby, mogą również ograniczać częstotliwość aktualizacji wizualnych. (Nie wszystkie malowanie jest wykonywane w wątku interfejsu użytkownika.

## <a name="run-the-html-ui-responsiveness-tool"></a>Uruchamianie narzędzia Responsywność interfejsu użytkownika HTML
 Narzędzie do reagowania interfejsu użytkownika HTML można użyć, gdy w programie Visual Studio jest otwarta działająca aplikacja platformy uniwersalnej systemu Windows.

1. Jeśli korzystasz z aplikacji z programu Visual Studio, na pasku narzędzi **Standardowy** na liście **Rozpocznij debugowanie** wybierz miejsce docelowe wdrożenia, takie jak **Komputer lokalny** lub **Urządzenie**.

2. W menu **Debugowanie** wybierz polecenie **Profiler wydajności**.

     Jeśli chcesz zmienić cel analizy dla profilera, wybierz pozycję **Zmień miejsce docelowe**.

     ![Zmień cel analizy](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Dla celu analizy dostępne są następujące opcje:

    - **Projekt startowy**. Wybierz tę opcję, aby przeanalizować bieżący projekt startowy. Jeśli używasz aplikacji na komputerze zdalnym lub urządzeniu zdalnym, musisz użyć tego ustawienia, które jest wartością domyślną.

    - **Uruchamianie aplikacji**. Wybierz tę opcję, aby wybrać aplikację platformy uniwersalnej systemu Windows z listy uruchomionych aplikacji. Nie można użyć tej opcji podczas uruchamiania aplikacji na komputerze zdalnym lub urządzeniu.

         Za pomocą tej opcji można analizować wydajność aplikacji uruchomionych na komputerze, gdy nie masz dostępu do kodu źródłowego.

    - **Zainstalowana aplikacja**. Wybierz tę opcję, aby wybrać zainstalowaną aplikację, którą chcesz przeanalizować. Nie można użyć tej opcji podczas uruchamiania aplikacji na komputerze zdalnym lub urządzeniu.

         Za pomocą tej opcji można analizować wydajność aplikacji zainstalowanych na komputerze, gdy nie masz dostępu do kodu źródłowego. Ta opcja może być również przydatna, gdy chcesz tylko analizować wydajność dowolnej aplikacji poza tworzeniem własnych aplikacji.

3. W **obszarze Dostępne narzędzia**wybierz pozycję Czas reakcji interfejsu użytkownika **HTML**, a następnie wybierz pozycję **Start**.

4. Po uruchomieniu programu Profilujas ui, okno Kontrola konta użytkownika może zażądać uprawnienia do uruchamiania programu Visual Studio ETW Collector.exe. Wybierz **pozycję Tak**.

     Interakcja z aplikacją, aby przetestować odpowiedni scenariusz wydajności. Aby uzyskać szczegółowy przepływ pracy, zobacz [Izolowanie problemu z odpowiedzią interfejsu użytkownika](#Workflow) i [wyizolowanie problemu z przepływnością wizualną](#IsolateVisualThroughput).

5. Przełącz się do programu Visual Studio, naciskając klawisze Alt+Tab.

6. Aby zatrzymać profilowanie aplikacji i wyświetlić dane zebrane przez profiler, wybierz pozycję **Zatrzymaj zbieranie**.

## <a name="isolate-an-issue"></a>Wyizolowanie problemu
 Poniższa sekcja zawiera sugestie ułatwiające wyizolowanie problemów z wydajnością. Aby uzyskać szczegółowe wyjaśnienie dotyczące sposobu identyfikowania i rozwiązywania problemów z wydajnością przy użyciu przykładowej aplikacji do testowania wydajności, zobacz [Przewodnik: Poprawianie reakcji interfejsu użytkownika (HTML).](html-ui-responsiveness.md)

### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a>Wyizolowanie problemu z odpowiedzią interfejsu użytkownika
 Te kroki zapewniają sugerowany przepływ pracy, który może pomóc w skuteczniejszym korzystaniu z profilera czas reakcji interfejsu użytkownika:

1. Otwórz aplikację w programie Visual Studio.

2. Przetestuj aplikację pod kątem problemów z odpowiedzią interfejsu użytkownika. (Naciśnij **klawisz Ctrl**+**F5,** aby uruchomić aplikację bez debugowania).

     Jeśli znajdziesz problem, kontynuuj testowanie, aby spróbować zawęzić przedział czasu, w którym występuje problem, lub spróbuj zidentyfikować wyzwalacze, które powodują zachowanie.

3. Przełącz się do **Alt**+programu Visual Studio (naciśnij**klawisz Alt Tab)** i zatrzymaj aplikację **(Shift**+**F5**).

4. Opcjonalnie należy dodać znaczniki użytkownika do kodu za pomocą [oznacz kod do analizy](#ProfileMark).

    > [!TIP]
    > Znaczniki użytkownika mogą pomóc w zidentyfikowaniu problemu z odpowiedzią podczas przeglądania danych profilera. Na przykład można dodać znacznik użytkownika na początku i na końcu sekcji kodu, która powoduje problem z odpowiedzią.

5. Uruchom profiler czas reakcji interfejsu użytkownika, postępując zgodnie z instrukcjami w poprzedniej sekcji.

6. Umieść aplikację w stanie, który powoduje problem z odpowiedzią interfejsu użytkownika.

7. Przełącz się do programu Visual Studio (naciśnij klawisze Alt+Tab) i wybierz pozycję **Zatrzymaj kolekcję** na karcie profiler profilera profilera profilowania.

8. Jeśli dodano znaczniki użytkownika, pojawią się one na [osi czasu sesji diagnostycznej](#Ruler) profilera. Na poniższej ilustracji przedstawiono pojedynczy znacznik użytkownika używany do określenia określonej operacji w kodzie.

     ![Linijka diagnostyki z oznaczenia użytkownika](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

9. Identyfikowanie obszaru zainteresowania na osi czasu i wykresów profilera przy użyciu znaczników użytkownika, zdarzeń cyklu życia aplikacji lub danych widocznych na wykresach. Oto kilka wskazówek ułatwiające analizowanie i używanie danych na wykresach:

    - Użyj [wyświetl oś czasu sesji diagnostycznej,](#Ruler) aby wyświetlić oznacz kod do [analizy,](#ProfileMark)zdarzenia cyklu życia aplikacji i skojarzoną oś czasu dla tych zdarzeń i oś czasu dla danych na innych wykresach.

    - Wykres [wykorzystania procesora CPU](#CPUUtilization) służy do wyświetlania ogólnych informacji o aktywności procesora i rodzaju pracy, jaką obsługuje w określonym okresie czasu. Okresy nadmiernej aktywności procesora CPU są bardziej prawdopodobne, aby spowodować problemy z responsywnością i porzucone ramki.

    - Jeśli tworzysz grę lub aplikację multimedialną, użyj [wyświetl przepływności wizualnej (FPS),](#VisualThroughput) aby zidentyfikować okresy, w których liczba klatek na sekundę spadła.

10. Zaznacz obszar zainteresowania na jednym z wykresów, klikając część wykresu i przeciągając wskaźnik, aby dokonać wyboru (lub za pomocą klawisza Tabulatora i klawiszy strzałek). Po wybraniu okresu przez dokonanie wyboru wykres szczegółów osi czasu w dolnym okienku profilera zmienia się, aby wyświetlić tylko wybrany okres.

     Na poniższej ilustracji przedstawiono wykres wykorzystania procesora CPU z wyróżnionym obszarem zainteresowania.

     ![Wykres wykorzystania procesora](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

11. Użyj [zobacz szczegóły osi czasu,](#TimelineDetails) aby uzyskać szczegółowe informacje o zdarzeniach, które są uruchomione zbyt często lub zajmuje zbyt dużo czasu, aby zakończyć. Na przykład poszukaj następujących elementów:

    - Detektory zdarzeń, czasomierze i wywołania zwrotne klatki animacji. W zależności od określonego zdarzenia podane dane mogą obejmować identyfikator zmodyfikowanych elementów DOM, nazwę zmodyfikowanych właściwości CSS, łącze do lokalizacji źródłowej oraz nazwę skojarzonego zdarzenia lub funkcji wywołania zwrotnego.

    - Zdarzenia układu lub skryptów, które spowodowały renderowanie `window.getComputedStyles`elementów, takich jak wywołania . Skojarzony element DOM dla zdarzenia jest podany.

    - Strony lub zasoby adresów URL, które są ładowane przez aplikację, takie jak oceny skryptów dla zdarzeń analizy HTML. Podana jest nazwa pliku lub zasób.

    - Inne zdarzenia określone w [odwołaniu do zdarzenia profilera](#profiler-event-reference).

    > [!TIP]
    > Większość użytecznych informacji w profilirze pojawia się na wykresie szczegółów osi czasu.

12. W obszarze wybranym na wykresie wykorzystania procesora CPU lub przepływności wizualnej (FPS) wybierz polecenie **Powiększenie** (menu przyciskowe lub kontekstowe), aby uzyskać bardziej szczegółowe informacje. Oś czasu wykresu zmienia się, aby wyświetlić tylko wybrany okres.

13. Po powiększeniu wybierz część wykresu wykorzystania procesora CPU lub przepływności wizualnej. Podczas dokonywania wyboru wykres szczegółów osi czasu w dolnym okienku profilera zmienia się, aby wyświetlić tylko wybrany okres czasu.

### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a>Wyizolowanie problemu z przepływnością wizualną
 Okresy nadmiernego wykorzystania procesora CPU mogą powodować niską lub niespójną liczbę klatek na sekundę. Jeśli opracujesz aplikacje i gry multimedialne, wykres przepływności wizualnej może dostarczyć ważniejszych danych niż wykres wykorzystania procesora CPU.

 Aby wyizolować problem przepływności wizualnej, wykonaj kroki opisane w poprzedniej sekcji, ale użyj wykresu przepływności wizualnej jako jednego z kluczowych punktów danych.

### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a>Oznacz kod do analizy
 Aby ułatwić wyizolowanie sekcji kodu aplikacji skojarzonej z danymi wyświetlanymi na wykresach, można dodać wywołanie funkcji w aplikacji, które nakazuje profilerowi wstawianie znacznika użytkownika — odwróconego trójkąta — na osi czasu w momencie wykonania funkcji. Każdy znak użytkownika, który można dodać pojawia się na osi czasu dla wykresu wykorzystania procesora CPU, wykres przepływności wizualnej i wykres szczegółów osi czasu.

 Aby dodać znacznik użytkownika, dodaj do aplikacji następujący kod. W tym przykładzie użyto "uzyskiwanie danych" jako opis zdarzenia.

```javascript
if (performance && performance.mark) {
    performance.mark("getting data");
}

```

 Opis zdarzenia pojawia się jako etykietka narzędzia po umieszczeniu wskaźnika myszy nad znakiem użytkownika. Można dodać dowolną liczbę znaczników użytkownika.

> [!NOTE]
> `console.timeStamp`, polecenie Chrome, pojawia się również jako znak użytkownika.

 Na poniższej ilustracji przedstawiono linijkę diagnostyczną z pojedynczym znakiem użytkownika i etykietką narzędzia.

 ![Linijka diagnostyki z oznaczenia użytkownika](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

 Można również utworzyć zdarzenia generowane przez narzędzia w widoku szczegółów osi czasu, aby pokazać czas, który przechodzi między dwoma znacznikami użytkownika. Poniższy kod dodaje drugi znacznik użytkownika i pomiar czasu, który przechodzi między wykonaniem dwóch znaków użytkownika (poprzedni kod pokazuje pierwszy znak użytkownika).

```javascript
if (performance.mark && performance.measure) {
    performance.mark("data retrieved");
    performance.measure("data measure", "getting data", "data retrieved");
}
```

 Jeśli drugi znacznik użytkownika nie `performance.measure` jest określony, używa sygnatury czasowej jako drugiego znacznika użytkownika. Wymagany jest pierwszy znak użytkownika.

 Pomiar czasu trwania jest wyświetlany jako zdarzenie **miara użytkownika** w widoku szczegółów osi czasu i zawiera szczegółowe informacje po wybraniu.

 ![Zdarzenie pomiaru użytkownika w widoku szczegółów osi czasu](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")

## <a name="analyze-data"></a>Analizowanie danych
 Poniższe sekcje zawierają informacje ułatwiające interpretację danych, które pojawiają się w profilerze.

### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a>Wyświetlanie osi czasu sesji diagnostycznej
 Linijka w górnej części profilera pokazuje oś czasu dla profilowanych informacji. Ta oś czasu dotyczy zarówno wykresu wykorzystania procesora CPU, jak i wykresu przepływności wizualnej.

 Oto jak wygląda oś czasu sesji diagnostycznej z etykietką narzędzia wyświetlaną dla kilku zdarzeń cyklu życia aplikacji:

 ![Linijka sesji diagnostycznej](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")

 Oś czasu pokazuje, kiedy zdarzenia cyklu życia aplikacji, takie jak zdarzenie aktywacji, występują i pokazuje znaki użytkownika (trójkąty znaczników użytkownika), które można dodać do kodu. Można wybrać zdarzenia, aby wyświetlić etykietki narzędzi z więcej informacji. Aby uzyskać więcej informacji na temat znaków użytkownika, zobacz [Oznaczanie kodu do analizy](#ProfileMark) w tym temacie.

 Zdarzenia cyklu życia aplikacji są wyświetlane jako symbole rombu. Są to zdarzenia DOM, które obejmują:

- `DOMContentLoaded`i `Load` zdarzenia, które zazwyczaj występują w aktywowanym programie obsługi zdarzeń w kodzie. Etykietka narzędzia dla zdarzenia pokazuje określone zdarzenie i adres URL.

- Zdarzenie nawigacji, które występuje podczas przechodzenia do innej strony. Etykietka narzędzia dla zdarzenia pokazuje adres URL strony docelowej.

### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a>Wyświetlanie wykorzystania procesora
 Wykres wykorzystania procesora CPU umożliwia identyfikowanie okresów czasu, w którym występuje nadmierna aktywność procesora CPU. Zawiera informacje o średnim zużyciu procesora CPU w aplikacji w okresie czasu. Informacje są oznaczone kolorami w celu przedstawienia następujących określonych kategorii: **Ładowanie**, **Skrypty**, wyrzucanie elementów bezużytecznych **(GC),** **Stylowanie,** **Renderowanie**i **Dekodowanie obrazu**. Aby uzyskać więcej informacji na temat tych kategorii, zobacz [Odwołanie do zdarzenia profilera](#profiler-event-reference) w dalszej części tego tematu.

 Wykres wykorzystania procesora CPU pokazuje ilość czasu spędzonego na wszystkich wątkach aplikacji, łącząc wartości wykorzystania procesora CPU dla jednego lub więcej procesorów w jedną wartość procentową. Wartość wykorzystania procesora CPU może przekroczyć 100 procent, gdy używany jest więcej niż jeden procesor.

> [!NOTE]
> Wykorzystanie gpu nie pojawia się na wykresie.

 W tym przykładzie pokazano, jak wygląda wykres wykorzystania procesora CPU:

 ![Wykres wykorzystania procesora](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

 Ten wykres służy do:

- Określ ogólne obszary budzące obawy.

- Wybierz określony okres do wyświetlenia na wykresie szczegółów osi czasu. Aby wybrać okres czasu, zaznacz część wykresu i przeciągnij wskaźnik, aby dokonać wyboru.

- Uzyskaj bardziej szczegółowy widok wybranego okresu, wybierając przycisk **Powiększ.**

  Aby uzyskać więcej informacji na temat korzystania z wykresu, zobacz [Izolowanie problem z odpowiedzią interfejsu użytkownika](#Workflow) w tym temacie.

### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a>Wyświetlanie przepływności wizualnej (FPS)
 Wizualny wykres przepływności umożliwia identyfikowanie okresów, w których liczba klatek na sekundę spadła. Pokazuje klatki na sekundę (FPS) dla aplikacji. Ten wykres jest najbardziej przydatny do tworzenia gier i aplikacji multimedialnych.

 Wyświetlana wartość FPS może różnić się od rzeczywistej liczby klatek na sekundę. Podczas badania danych na tym wykresie należy pamiętać o tych informacjach:

- Wykres pokazuje FPS, że aplikacja jest w stanie osiągnąć w określonym czasie. Gdy aplikacja jest bezczynna, fps jest taka sama jak częstotliwość odświeżania monitora.

- Wykres pokazuje rzeczywiste FPS, jeśli aplikacja wykonuje pracę, która wymaga aktualizacji wizualnych.

- Wykres pokazuje wartość zero, jeśli klatki są odrzucane.

  W tym przykładzie pokazano, jak wygląda wykres przepływności wizualnej:

  ![Wykres przepływności wizualnej](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")

  Wykres przepływności wizualnej służy do:

- Określ ogólne obszary budzące obawy.

- Wybierz określony okres do wyświetlenia na wykresie szczegółów osi czasu. Aby wybrać okres czasu, zaznacz część wykresu i przeciągnij wskaźnik, aby dokonać wyboru.

- Uzyskaj bardziej szczegółowy widok wybranego okresu, wybierając przycisk **Powiększ.**

### <a name="view-timeline-details"></a><a name="TimelineDetails"></a>Wyświetlanie szczegółów osi czasu
 Wykres szczegółów osi czasu pojawia się w dolnym okienku profilera czas reakcji interfejsu użytkownika. Zawiera sekwencyjne i hierarchiczne informacje o zdarzeniach, które zużywały najwięcej czasu procesora CPU w wybranych okresach. Ten wykres może pomóc określić, co wyzwoliło określone zdarzenie, a w przypadku niektórych zdarzeń, jak zdarzenie mapuje z powrotem do kodu źródłowego. Ten wykres pomaga również określić czas wymagany do malowania aktualizacji wizualnych na ekranie.

 Wykres przedstawia pracę wątku interfejsu użytkownika i pracy na wątki w tle, które mogą przyczynić się do powolnych aktualizacji wizualnych. Wykres nie pokazuje pracy JIT JavaScript, asynchronicznego pracy procesora GPU, pracy wykonywanej poza procesem hosta (na przykład RuntimeBroker.exe i dwm.exe work) ani pracy dla obszarów środowiska wykonawczego systemu Windows, które nie zostały jeszcze zaaranżowane do profilowania (takich jak we/wy dysku).

> [!TIP]
> Gdy zdarzenie występuje w wątku tła, identyfikator wątku pojawia się w nawiasach obok nazwy zdarzenia.

 W tym przykładzie pokazano, jak wygląda wykres szczegółów osi czasu po wybraniu odbiornika zdarzeń dla zdarzenia kliknięcia DOM:

 ![Wykres szczegółów osi czasu](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")

 Na tej ilustracji **spinAction** obsługi zdarzeń w kolumnie **Nazwa zdarzenia** jest łącze, które po wybraniu spowoduje, że do obsługi zdarzeń w kodzie źródłowym. W prawym okienku właściwość **funkcji wywołania zwrotnego** zawiera to samo łącze do kodu źródłowego. Inne właściwości zawierają również informacje o zdarzeniu, takie jak skojarzony element DOM.

 Jeśli wybierzesz część osi czasu dla wykresu wykorzystania procesora CPU i przepływności wizualnej (FPS), wykres szczegółów osi czasu zawiera szczegółowe informacje dotyczące wybranego okresu.

 Zdarzenia na wykresie szczegółów osi czasu są oznaczone kolorami, aby reprezentować te same kategorie pracy, które są wyświetlane na wykresie wykorzystania procesora CPU. Aby uzyskać więcej informacji na temat kategorii zdarzeń i określonych zdarzeń, zobacz [Odwołanie do zdarzenia profilera](#profiler-event-reference) w tym temacie.

 Wykres szczegółów osi czasu służy do:

- Wyświetlanie przybliżonych godzin rozpoczęcia, czasu trwania i czasu zakończenia zdarzenia w widoku osi czasu i siatki. Wykres szczegółów osi czasu może wyświetlać okresy od 30 milisekund do 30 sekund w widoku siatki, w zależności od stanu powiększenia. Dla wartości czasu trwania:

  - Czasy włącznie reprezentują czas trwania zdarzenia, w tym zdarzenia podrzędnego. W widoku siatki ta wartość pojawia się jako pierwsza.

  - Czasy wyłączności reprezentują czas trwania zdarzenia, z wyłączeniem zdarzeń podrzędnych. W widoku siatki ta wartość jest wyświetlana w nawiasach.

- Rozwiń zdarzenie w hierarchii, aby wyświetlić element podrzędny zdarzenia. Element podrzędny zdarzenia są inne zdarzenia, które są wywoływane przez zdarzenie nadrzędne. Na przykład zdarzenie DOM może mieć detektory zdarzeń, które są wyświetlane jako dzieci. Detektor zdarzeń może mieć inne zdarzenia, które wynikają z niego, takie jak zdarzenie układu.

- Sortowanie zdarzeń według czasu rozpoczęcia (domyślnego) lub czasu trwania. Użyj listy **Sortuj według,** aby wybrać metodę sortowania.

- Wyświetl szczegóły dla każdego zdarzenia w okienku szczegółów (prawe okienko). Właściwości różnią się w zależności od konkretnego zdarzenia, jak pokazują te przykłady:

  - Dla czasomierzy, detektory zdarzeń (zdarzenia DOM) i wywołania zwrotne ramki animacji **właściwość Wywołanie zwrotne** udostępnia łącze do lokalizacji kodu źródłowego wraz z nazwą programu obsługi zdarzeń lub funkcji wywołania zwrotnego.

  - W przypadku czasomierzy, detektorów zdarzeń (zdarzeń DOM), zdarzeń układu i wywołań zwrotnych w klatce animacji, w sekcji **Podsumowanie czasu włącznie** (pierścień oznaczony kolorami) pojawi się oznaczone kolorami podsumowanie wybranego zdarzenia i wszystkich jego obrażeń. Każdy kolorowy wycinek obrazu reprezentuje typ zdarzenia. Etykietki narzędzi podają nazwę typu zdarzenia.

  > [!TIP]
  > Wykres szczegółów osi czasu i **podsumowanie czasu włącznie** mogą pomóc w zidentyfikowaniu obszarów do optymalizacji. Jeśli którykolwiek z tych widoków pokazuje dużą liczbę małych zadań, zdarzenie może być kandydatem do optymalizacji. Na przykład aplikacja może często odświeżać elementy DOM, co powoduje dużą liczbę zdarzeń analizy układu i HTML. Możesz zoptymalizować wydajność, wsadując tę pracę.

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a>Filtrowanie szczegółów osi czasu
 Widok w szczegółach osi czasu można filtrować do określonego zdarzenia, wybierając **opcję Filtruj do zdarzenia** z menu kontekstowego dla określonego zdarzenia. Po wybraniu tej opcji oś czasu i widok siatki są ograniczone do wybranego zdarzenia. Wybór na wykresie wykorzystania procesora CPU również zakresy do określonego zdarzenia.

 ![Filtrowanie osi czasu do zdarzenia](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")

### <a name="filter-events"></a><a name="FilterEvents"></a>Filtrowanie zdarzeń
 Można odfiltrować niektóre zdarzenia z wykresu szczegółów osi czasu, aby zmniejszyć szum w danych lub wyeliminować dane, które nie są interesujące dla scenariusza wydajności. Możesz filtrować według nazwy zdarzenia lub czasu trwania zdarzenia lub według określonych filtrów opisanych tutaj.

 Aby odfiltrować dekodowanie obrazu, pobieranie spekulacyjne i zdarzenia GC, wyczyść opcję **Aktywność w tle** z ikony filtru w dolnym okienku. Ponieważ te zdarzenia nie są bardzo zas można wykonać, są one domyślnie ukryte.

 ![Filtrowanie zdarzeń na osi czasu](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")

 Aby odfiltrować zdarzenia żądania HTTP, wyczyść opcję **Ruch sieciowy** z ikony filtru w dolnym okienku. Domyślnie te zdarzenia są wyświetlane na wykresie szczegółów osi czasu.

 Aby odfiltrować działanie wątku interfejsu użytkownika, wyczyść opcję **działania interfejsu użytkownika.**

> [!TIP]
> Wyczyść tę opcję i wybierz opcję Ruch sieciowy, aby zbadać problemy związane z opóźnieniem sieci.

 Aby odfiltrować miary użytkownika, wyczyść opcję **Miary użytkownika.** Miary użytkownika są zdarzeniami najwyższego poziomu bez obrażeń od dzieci.

### <a name="group-events-by-frame"></a><a name="GroupFrames"></a>Grupowanie zdarzeń według ramek
 Zdarzenia wyświetlane w widoku szczegółów osi czasu można grupować do poszczególnych klatek. Te zdarzenia ramki są zdarzenia generowane przez narzędzie i reprezentują kontenery zdarzeń najwyższego poziomu dla wszystkich prac wątku interfejsu użytkownika, która występuje między zdarzeniami malowania. Aby włączyć ten widok, wybierz **pozycję Grupuj zdarzenia najwyższego poziomu według ramek**.

 ![Grupowanie zdarzeń najwyższego poziomu według ramki](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")

 Podczas grupowania zdarzeń według ramki zdarzenia najwyższego poziomu w szczegółach osi czasu wyświetlają ramkę.

 ![Zdarzenia osi czasu pogrupowane według ramki](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")

## <a name="save-a-diagnostic-session"></a>Zapisywanie sesji diagnostycznej
 W programie Visual Studio można zapisać sesję diagnostyczną po zamknięciu karty, która jest skojarzona z sesją. Zapisane sesje można ponownie otworzyć w późniejszym czasie.

## <a name="profiler-event-reference"></a>Odwołanie do zdarzenia profilera
 Zdarzenia profilera są klasyfikowane i oznaczone kolorami w profilerze responsywności interfejsu użytkownika. Oto kategorie zdarzeń:

- **Ładowania.** Wskazuje czas poświęcony na pobieranie zasobów aplikacji i analizowanie html i CSS podczas pierwszego ładowania aplikacji. Może to obejmować żądania sieciowe.

- **Skryptów.** Wskazuje czas spędzony na analizowaniu i uruchamianiu języka JavaScript. Obejmuje to zdarzenia DOM, czasomierze, ocenę skryptów i pracę nad ramką animacji. Zawiera zarówno kod użytkownika, jak i kod biblioteki.

- **Gc.** Wskazuje czas spędzony na wyrzucaniu elementów bezużytecznych.

- **Stylizacji.** Wskazuje czas spędzony na analizowaniu CSS i obliczaniu prezentacji i układu elementu.

- **Renderowania.** Wskazuje czas spędzony na malowaniu ekranu.

- **Dekodowanie obrazu.** Wskazuje czas spędzony na dekompresji i dekodowaniu obrazów.

  W przypadku kategorii skryptów i stylów profiler czas reakcji interfejsu użytkownika może dostarczyć danych, na których można działać na wykresie szczegółów osi czasu. Jeśli problem zidentyfikujesz jako problem, możesz uruchomić profilator próbkowania procesora CPU za pomocą profilera czas reakcji interfejsu użytkownika. Alternatywnie można użyć profilera funkcji programu Visual Studio, aby uzyskać bardziej szczegółowe dane. Aby uzyskać więcej informacji, zobacz [Pamięć JavaScript](../profiling/javascript-memory.md).

  W przypadku innych kategorii zdarzeń można zidentyfikować skutki uboczne platformy, które wynikają z dodawania funkcji do aplikacji, ale w takich przypadkach może nie być w stanie rozwiązać określonych problemów z wydajnością przy użyciu profilera czas reakcji interfejsu użytkownika.

  W poniższej tabeli przedstawiono zdarzenia i ich opisy:

|Wydarzenie|Kategoria zdarzenia|Występuje, gdy|
|-----------|--------------------|-----------------|
|Analizowanie CSS|Ładowania|Napotkano nową zawartość CSS i podjęto próbę przeanalizowania zawartości CSS.|
|Analizowanie HTML|Ładowania|Napotkano nową zawartość HTML i podjęto próbę przeanalizowania zawartości w węzłach i wstawienia zawartości do drzewa DOM.|
|Żądanie HTTP|Ładowania|W domu znaleziono zdalny zasób lub utworzono żądanie XMLHttpRequest, które spowodowało żądanie HTTP.|
|Pobieranie spekulacyjne|Ładowania|Zawartość HTML strony została przeszukana w poszukiwaniu wymaganych zasobów, dzięki czemu można było szybko zaplanować kolejne żądania HTTP dla zasobów.|
|Funkcja wywołania zwrotnego klatki animacji|Wykonywanie skryptów|Przeglądarka miała renderować inną ramkę, co wyzwoliło funkcję wywołania zwrotnego dostarczoną przez aplikację.|
|Zdarzenie DOM|Wykonywanie skryptów|Wystąpiło zdarzenie DOM i zostało wykonane.<br /><br /> Właściwość `context` zdarzenia DOM, na `DOMContentLoaded` `click`przykład lub , jest wyświetlana w nawiasach.|
|Detektor zdarzeń|Wykonywanie skryptów|Odbiornik zdarzeń został wywołany i wykonany.|
|Odbiornik zapytań o media|Wykonywanie skryptów|Zarejestrowana kwerenda multimedialna została unieważniona, co spowodowało wykonanie skojarzonego z nim odbiornika(-ów).|
|Obserwator mutacji|Wykonywanie skryptów|Jeden lub więcej obserwowanych elementów DOM zostały zmodyfikowane, co spowodowało wykonanie mutationObserver skojarzone wywołania zwrotnego.|
|Ocena skryptu|Wykonywanie skryptów|Nowy element SCRIPT został znaleziony w dom i podjęto próbę przeanalizowania i wykonania skryptu.|
|Czasomierz|Wykonywanie skryptów|Upłynął zaplanowany czasomierz, co spowodowało wykonanie skojarzonej z nim funkcji wywołania zwrotnego.|
|Funkcja wywołania zwrotnego asynchronii środowiska wykonawczego systemu Windows|Wykonywanie skryptów|Operacja asynchronizowana, `Promise` która wyzwoliła funkcję wywołania zwrotnego, została ukończona przez obiekt środowiska wykonawczego systemu Windows.|
|Zdarzenie środowiska wykonawczego systemu Windows|Wykonywanie skryptów|Zdarzenie, które wystąpiło w obiekcie środowiska wykonawczego systemu Windows wyzwoliło zarejestrowany odbiornik.|
|Wyrzucanie elementów bezużytecznych|GC|Czas poświęcony na zbieranie pamięci dla obiektów, które nie były już używane.|
|Obliczenia CSS|Style|Wprowadzono zmiany w modelu DOM, które wymagały ponownego obliczenia właściwości stylu wszystkich elementów, których dotyczy problem.|
|Układ|Style|Wprowadzono zmiany w modelu DOM, które wymagały ponownego obliczenia rozmiaru i/lub położenia wszystkich elementów, których dotyczy problem.|
|Farby|Renderowanie|Wprowadzono zmiany wizualne w dom i podjęto próbę ponownego renderowania części strony.|
|Renderuj warstwę|Renderowanie|Zmiany wizualne zostały wprowadzone do niezależnie renderowanego fragmentu dom (zwanego warstwą), a zmiany wymagały renderowania części strony.|
|Dekodowanie obrazu|Dekodowanie obrazu|Obraz został dołączony do modelu DOM i podjęto próbę dekompresji i dekodowania obrazu z oryginalnego formatu na mapę bitową.|
|Klatka|Nie dotyczy|Wprowadzono zmiany wizualne w dom, który wymagał ponownego narysowania wszystkich części strony, których dotyczy problem. Jest to zdarzenie generowane przez narzędzie używane do grupowania.|
|Miara użytkownika|Nie dotyczy|Scenariusz specyficzne dla aplikacji został `performance.measure` zmierzony przy użyciu metody. Jest to zdarzenie generowane przez narzędzie używane do analizowania kodu.|

## <a name="additional-information"></a>Dodatkowe informacje

- Obejrzyj [ten film wideo](https://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Kompilacja 2013 na temat profilera responsywności interfejsu użytkownika.

- Przeczytaj wskazówki dotyczące wydajności aplikacji platformy uniwersalnej systemu Windows utworzonych dla systemu Windows przy użyciu języka JavaScript. Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące wydajności aplikacji platformy uniwersalnej systemu Windows przy użyciu języka JavaScript](/previous-versions/windows/apps/hh465194\(v\=win.10\)).

- Aby uzyskać informacje na temat modelu wykonywania kodu jednowątkowego i wydajności, zobacz [Wykonywanie kodu](/previous-versions/windows/apps/hh781217\(v\=win.10\)).

## <a name="see-also"></a>Zobacz też
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
