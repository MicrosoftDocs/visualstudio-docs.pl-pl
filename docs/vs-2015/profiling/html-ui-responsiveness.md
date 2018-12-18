---
title: Czas odpowiedzi interfejsu użytkownika HTML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 63027ccfffde0aa3b62bae6c1529826fd9b26c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760717"
---
# <a name="html-ui-responsiveness"></a>Czas odpowiedzi interfejsu użytkownika HTML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak można wyizolować problemy z wydajnością w aplikacjach przy użyciu Profiler czasu odpowiedzi interfejsu użytkownika, narzędzie wydajność, dostępne dla aplikacji Windows Universal.  
  
 Profiler czasu odpowiedzi interfejsu użytkownika mogą pomóc wyizolować problemy, takie jak problemy dotyczące czasu odpowiedzi interfejsu użytkownika lub platformy efekty uboczne, które zazwyczaj występują z tych objawów:  
  
-   Brak czasu odpowiedzi w interfejsie użytkownika. Aplikacja może być wolne odpowiedzi, jeśli jest blokowana w wątku interfejsu użytkownika. Kilka rzeczy, które mogą zablokować wątek interfejsu użytkownika obejmują nadmierne synchroniczny kod JavaScript, nadmierne układ CSS lub pracy obliczeń CSS, żądań synchronicznych XHR, wyrzucanie elementów bezużytecznych, czasy nadmierne paint lub kod JavaScript obciążającą procesor.  
  
-   Wolne ładowanie aplikacji lub strony. Zazwyczaj jest to spowodowane zbyt czas ładowania zasobów.  
  
-   Aktualizacje wizualne, które są rzadsze, niż oczekiwano. Dzieje się tak, jeśli wątek interfejsu użytkownika jest zbyt zajęty, aby zachować płynne szybkości. Na przykład jeśli wątek interfejsu użytkownika jest zajęty, ramki mogą być opuszczane. Niektóre wątek bez interfejsu użytkownika działają, takie jak żądania sieci, dekodowanie obrazu, oraz farby można również ograniczyć częstotliwość aktualizacji visual. (Nie wszystkie malowanie odbywa się w wątku interfejsu użytkownika).  
  
##  <a name="RunningProfiler"></a> Uruchom narzędzie czas odpowiedzi interfejsu użytkownika HTML  
 Można użyć narzędzia HTML UI Responsiveness, gdy masz działającą aplikację Windows Universal lub Windows Store, Otwórz w programie Visual Studio lub zainstalowanych na komputerze z systemem Windows 8 lub nowszym.  
  
1.  Jeśli korzystasz z aplikacji z programu Visual Studio, na **standardowa** narzędzi w **Rozpocznij debugowanie** wybierz cel wdrożenia, takich jak jeden z emulatory Windows Phone, **komputera lokalnego** , **Symulator**, lub **maszyny zdalnej**.  
  
2.  Na **debugowania** menu, wybierz **Profiler wydajności...** .  
  
     Jeśli chcesz zmienić cel analizy programu Profiler, wybierz opcję**zmienić docelowy**.  
  
     ![Zmień cel analizy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Poniższe opcje są dostępne dla obiektu docelowego analizy:  
  
    -   **Projekt startowy**. Wybierz tę opcję, aby analizować bieżący projekt startowy. Po uruchomieniu aplikacji na komputerze zdalnym lub urządzeniu, należy użyć tego ustawienia, która jest wartością domyślną.  
  
    -   **Twoja aplikacja działa**. Wybierz tę opcję, aby wybrać aplikację Windows Store z listy uruchomionych aplikacji. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym lub urządzeniu.  
  
         Ta opcja służy do analizowania wydajności aplikacji, które są uruchomione na komputerze, gdy nie masz dostępu do kodu źródłowego.  
  
    -   **Zainstalowana aplikacja**. Wybierz tę opcję, aby wybrać zainstalowaną aplikację, które mają być analizowane. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym lub urządzeniu.  
  
         Ta opcja służy do analizowania wydajności aplikacji, które zainstalowano na tym komputerze, gdy nie masz dostępu do kodu źródłowego. Ta opcja również może być przydatne podczas po prostu chcesz analizować wydajność aplikacji poza tworzenie aplikacji.  
  
3.  Z **dostępnych narzędzi**, wybierz opcję **HTML UI Responsiveness**, a następnie wybierz **Start**.  
  
4.  Kiedy uruchamiasz Profiler czasu odpowiedzi interfejsu użytkownika, okno Kontrola konta użytkownika może zażądać Twojej zgody, aby uruchomić program Visual Studio ETW Collector.exe. Wybierz **tak**.  
  
     Wchodzić w interakcje z aplikacją, aby przetestować scenariusz odpowiednie działania. Aby uzyskać szczegółowy przepływ pracy, zobacz [wyizolować problem czasu odpowiedzi interfejsu użytkownika](#Workflow) i [wyizolować problem przepustowość wizualna](#IsolateVisualThroughput).  
  
5.  Przełącz się do programu Visual Studio, naciskając klawisze Alt + Tab.  
  
6.  Aby zatrzymać profilowanie aplikacji i przeglądanie danych, który program profilujący zebrane, wybierz **Zatrzymaj Kolekcjonowanie**.  
  
##  <a name="IsolateAnIssue"></a> Izolowanie problemu  
 W poniższej sekcji przedstawiono sugestie ułatwiające wyizolować problemy z wydajnością. Uzyskać szczegółowe informacje dotyczące identyfikowanie i rozwiązywanie problemów z wydajnością za pomocą aplikacji testowania wydajnościowego przykładowe, zobacz [wskazówki: poprawa UI responsiveness (HTML)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
###  <a name="Workflow"></a> Wyizolować problem czasu odpowiedzi interfejsu użytkownika  
 Poniższe kroki zawierają sugerowane przepływu pracy, które mogą ułatwić bardziej efektywne wykorzystanie Profiler czasu odpowiedzi interfejsu użytkownika:  
  
1.  Otwórz aplikację w programie Visual Studio.  
  
2.  Przetestuj swoją aplikację w przypadku problemów czasu odpowiedzi interfejsu użytkownika. (Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację bez debugowania).  
  
     Jeśli znajdziesz problem, można kontynuować testowanie próby Zawęź przedział czasu, w której występuje ten problem, lub do identyfikowania wyzwalacze, które powodują zachowanie.  
  
3.  Przełącz się do programu Visual Studio (naciśnij klawisze Alt + Tab) i Zatrzymaj aplikację (Shift + F5).  
  
4.  Opcjonalnie możesz dodać znaczniki użytkownika do kodu za pomocą [oznaczyć kodu do analizy](#ProfileMark).  
  
    > [!TIP]
    >  Znaczniki użytkownika może pomóc w zidentyfikowaniu problemu czas odpowiedzi podczas przeglądania danych profilera. Na przykład można dodać znacznik użytkownika na początku i na końcu sekcji kodu, który powoduje problem z czasem odpowiedzi.  
  
5.  Postępując zgodnie z instrukcjami w poprzedniej sekcji, aby uruchomić Profiler czas odpowiedzi interfejsu użytkownika.  
  
6.  Umieść ją w stan, który powoduje problem z czasem odpowiedzi interfejsu użytkownika.  
  
7.  Przejdź do programu Visual Studio (naciśnij klawisze Alt + Tab) i wybierz **Zatrzymaj Kolekcjonowanie** na karcie profiler Profiler czasu odpowiedzi interfejsu użytkownika.  
  
8.  Po dodaniu znaczniki użytkownika pojawią się one w [Wyświetl oś czasu sesji diagnostycznej](#Ruler) programu profilującego. Poniższa ilustracja przedstawia znakiem pojedynczego użytkownika, używany do określenia określoną operacją w kodzie.  
  
     ![Wyświetlanie znacznik użytkownika linijki diagnostyki](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Określ obszar zainteresowania osi czasu i wykresy profilera przy użyciu znaczniki użytkownika, zdarzenia cyklu życia aplikacji lub danych jest widoczny na wykresach. Poniżej przedstawiono kilka wskazówek, aby ułatwić analizowanie i korzystać z danych na wykresach:  
  
    -   Użyj [Wyświetl oś czasu sesji diagnostycznej](#Ruler) do wyświetlania [oznaczyć kodu do analizy](#ProfileMark), zdarzenia cyklu życia aplikacji, a skojarzone oś czasu dla tych zdarzeń i oś czasu dla danych w innych wykresów.  
  
    -   Użyj [Wykres wykorzystania procesora CPU](#CPUutilization) Aby wyświetlić ogólne informacje o aktywności Procesora i typu pracy obsługuje ich w określonym okresie. Okresy nadmierną aktywność procesora CPU są bardziej prawdopodobne spowodować problemy z czas reakcji i porzucić ramek.  
  
    -   Przypadku tworzenia aplikacji gier lub zaawansowanych nośnika, należy użyć [widoku przepustowość wizualna (kl. / s)](#VisualThroughput) do identyfikacji okresów czasu, w którym porzucony szybkość klatek.  
  
10. Wybierz obszar zainteresowania w jednym z wykresów, klikając częścią wykresu będącego i przeciągając wskaźnik, aby dokonać wyboru (lub za pomocą klawisza Tab i klawiszy strzałek). Po wybraniu okres czasu, dokonując wyboru, wykres szczegóły osi czasu w dolnym okienku programu profilującego zmienia się, aby pokazać tylko wybrany okres czasu.  
  
     Poniższa ilustracja przedstawia Wykres wykorzystania procesora CPU z obszaru zainteresowania wyróżnione.  
  
     ![CPU utilization graph](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
11. Użyj [wyświetlić szczegóły osi czasu](#TimelineDetails) Aby uzyskać szczegółowe informacje o zdarzeniach, które są uruchamiane zbyt często albo zajmuje zbyt dużo czasu, aby zakończyć. Na przykład Znajdź poniższe pozycje:  
  
    -   Odbiorniki zdarzeń, czasomierze i wywołania zwrotne ramek animacji. W zależności od określonego zdarzenia dostarczone dane mogą obejmować identyfikator zmodyfikowane elementy modelu DOM, nazwę właściwości CSS zmodyfikowany, łącza do lokalizacji źródłowej i nazwa funkcji skojarzone zdarzenie lub wywołania zwrotnego.  
  
    -   Układ i skrypty zdarzenia, które spowodowały renderowania elementów, takich jak wywołania `window.getComputedStyles`. Podano skojarzonego elementu DOM w wydarzeniu.  
  
    -   Strony lub zasobów adresu URL, które są ładowane za pomocą aplikacji, takich jak oceny skryptu dla analizuje zdarzenia w formacie HTML. Nazwa pliku lub zasobu jest dostarczany.  
  
    -   Inne zdarzenia, określone w [odwołanie do zdarzenia Profiler](#ProfilerEvents).  
  
    > [!TIP]
    >  Najbardziej użyteczne informacje w profilerze pojawia się na wykresie szczegółów osi czasu.  
  
12. Z obszarem wybranych w wykorzystanie procesora CPU lub wykres przepustowość wizualna (kl. / s), wybierz **powiększyć** (przycisk lub kontekst menu), aby uzyskać więcej szczegółowych informacji. Oś czasu dla zmian grafu pokazać tylko wybrany okres czasu.  
  
13. Podczas powiększono, należy wybrać część wykorzystanie procesora CPU lub przepustowość wizualna wykresu. Po dokonaniu wyboru, wykres osi czasu szczegóły profilera dolnym okienku zmieni się na Pokaż tylko wybrany okres czasu.  
  
###  <a name="IsolateVisualThroughput"></a> Wyizolować problem przepustowość wizualna  
 Okresy intensywne użycie procesora CPU może spowodować szybkości klatek niski lub niespójne. W przypadku tworzenia bogatych multimediów aplikacje i gry, wykres przepustowość wizualna może dostarczyć danych ważniejsze niż wykres wykorzystania procesora CPU.  
  
 Aby wyizolować problem przepustowość wizualna, wykonaj czynności opisane w poprzedniej sekcji, ale za pomocą wykresu przepustowość wizualna jako jeden do kluczowych punktów danych.  
  
###  <a name="ProfileMark"></a> Kod znaku do analizy  
 Aby wyizolować części kodu aplikacji, który jest skojarzony z danymi, która pojawia się na wykresach, można dodać wywołania funkcji w aplikacji, która powoduje, że profiler, aby wstawić znacznik użytkownika — odwrócony trójkąt — na osi czasu w tej chwili funkcja pobiera uruchomiona. Każdego znaku użytkownika, który dodajesz pojawia się na osi czasu, Wykres wykorzystania procesora CPU, wykres przepustowość wizualna i wykres szczegóły osi czasu.  
  
 Aby dodać znacznik użytkownika, należy dodać następujący kod do aplikacji. W tym przykładzie używa "Pobieranie danych" jako opis zdarzenia.  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Opis zdarzenia jest wyświetlany jako etykietka narzędzia, po umieszczeniu wskaźnika myszy nad znacznik użytkownika. Możesz dodać dowolną liczbę znaczniki użytkownika, ile potrzebujesz.  
  
> [!NOTE]
>  `console.timeStamp`, polecenia dla programu Chrome, są także przedstawione jako znacznik użytkownika.  
  
 Poniższa ilustracja przedstawia Linijka diagnostyki ze znakiem pojedynczego użytkownika i jego etykietek narzędzi.  
  
 ![Wyświetlanie znacznik użytkownika linijki diagnostyki](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 W widoku szczegółów osi czasu, aby wyświetlić czas trwania czas, jaki upływa między dwa znaczniki użytkownika, można również utworzyć zdarzenia generowane przez narzędzie. Poniższy kod dodaje drugi znacznik użytkownika i pomiaru czas, jaki upływa między wykonaniem ze znakami dwóch użytkowników (poprzedni kod Pokazuje pierwszy znacznik użytkownika).  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 Jeśli drugi znacznik użytkownika nie jest określona, `performance.measure` używa sygnaturę czasową jako drugi znacznik użytkownika. Pierwszy znacznik użytkownika jest wymagana.  
  
 Pomiar czasu trwania jest wyświetlany jako **miara użytkownika** zdarzeń na osi czasu widoku szczegółów i zawiera szczegółowe informacje, w przypadku wybrania.  
  
 ![Widok szczegółów zdarzenia miara użytkownika na osi czasu](../profiling/media/js-htmlvizprofiler-user-measure.png "JS_HTMLVizProfiler_User_Measure")  
  
##  <a name="AnalyzeData"></a> Analizowanie danych  
 Poniższe sekcje zawierają informacje pomocne w interpretacji danych, który pojawia się w profilerze.  
  
###  <a name="Ruler"></a> Wyświetl oś czasu sesji diagnostycznej  
 Linijka u góry profiler pokazuje oś czasu dla profilowanych informacji. Ta oś czasu dotyczy zarówno Wykres wykorzystania procesora CPU, jak i wykres przepustowość wizualna.  
  
 Oto jak wygląda oś czasu sesji diagnostycznej z etykietki narzędzia wyświetlany dla kilku zdarzenia cyklu życia aplikacji:  
  
 ![Linijka sesji diagnostycznej](../profiling/media/js-htmlvizprof-ruler.png "JS_HTMLVizProf_Ruler")  
  
 Przedstawia oś czasu, po wystąpieniu zdarzenia lifecyle aplikacji, takich jak zdarzenia aktywacji i pokazuje, że znaczniki użytkownika (trójkąty znacznik użytkownika) możesz dodać do kodu. Możesz wybrać zdarzeń do wyświetlenia etykietki narzędzi z większą ilością informacji. Aby uzyskać więcej informacji na temat znaczniki użytkownika, zobacz [oznaczyć kodu do analizy](#ProfileMark) w tym temacie.  
  
 Zdarzenia cyklu życia aplikacji są wyświetlane jako symbole romb. Są to zdarzenia modelu DOM, m.in:  
  
-   `DOMContentLoaded` i `Load` zdarzenia, które zazwyczaj występują w obsłudze zdarzeń aktywowane w kodzie. Etykietka narzędzia dla zdarzenia zawiera określonego zdarzenia i adres URL.  
  
-   Zdarzenie nawigacji, które występuje, gdy przejdziesz do innej strony. Etykietka narzędzia dla zdarzenia zawiera docelowy adres URL strony.  
  
###  <a name="CPUUtilization"></a> Wykorzystanie procesora CPU widoku  
 Wykres wykorzystania procesora CPU umożliwia określenie okresy czasu, w którym ma nadmierną aktywność procesora CPU. Zawiera informacje o aplikacji średnie użycie Procesora w danym okresie czasu. Informacje są oznaczone kolorami do reprezentowania następujące kategorie określonego: **ładowania**, **skryptów**, wyrzucanie elementów bezużytecznych (**GC**), **stylów**, **Renderowania**, i **dekodowanie obrazu**. Aby uzyskać więcej informacji na temat tych kategorii, zobacz [odwołanie do zdarzenia Profiler](#ProfilerEvents) w dalszej części tego tematu.  
  
 Wykres wykorzystania procesora CPU pokazuje ilość czasu poświęconego na wszystkich wątków aplikacji, łącząc wartości wykorzystanie procesora CPU dla jednego lub więcej procesorów CPU w pojedynczej wartości procentowej. Wartość wykorzystanie Procesora może przekroczyć 100 procent, gdy używany jest więcej niż jednego Procesora.  
  
> [!NOTE]
>  Użycie procesora GPU nie są wyświetlane na wykresie.  
  
 Ten przykład pokazuje, jak wygląda Wykres wykorzystania procesora CPU:  
  
 ![CPU utilization graph](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
 Użyj tego wykresu, aby:  
  
- Określ ogólne obszary zainteresowania.  
  
- Wybierz określonego przedziału czasu do wyświetlenia na wykresie szczegółów osi czasu. Aby wybrać okres czasu, wybierz częścią wykresu, a następnie przeciągnij wskaźnik, aby dokonać wyboru.  
  
- Uzyskać bardziej szczegółowy widok w wybranym okresie, wybierając **powiększyć** przycisku.  
  
  Aby uzyskać więcej informacji na temat korzystania z programu graph, zobacz [wyizolować problem czasu odpowiedzi interfejsu użytkownika](#Workflow) w tym temacie.  
  
###  <a name="VisualThroughput"></a> Wyświetl przepustowość wizualna (kl. / s)  
 Wykres przepustowość wizualna umożliwiają zidentyfikowanie okresy czasu, w którym porzucony szybkość klatek. Pokazuje liczbę klatek na sekundę (kl. / s) dla aplikacji. Ten wykres jest najbardziej użyteczne dla opracowywania gier i multimediów aplikacji.  
  
 Wyświetlana wartość kl. / s może różnić się od liczba klatek na sekundę. Podczas badania danych na tym wykresie, należy pamiętać o tych informacji:  
  
- Na wykresie widać kl. / s, czy aplikacja ma możliwość osiągnięcia określonej godzinie. Gdy aplikacja jest w stanie bezczynności, kl. / s jest taka sama jak częstotliwość odświeżania monitora.  
  
- Na wykresie przedstawiono rzeczywiste kl. / s, jeśli pracy, który wymaga aktualizacji visual działania aplikacji.  
  
- Na wykresie widać wartość zero, jeśli ramki są usuwane.  
  
  Ten przykład pokazuje, jak wygląda wykres przepustowość wizualna:  
  
  ![Wykres przepustowość wizualna](../profiling/media/js-htmlvizprof-vizthru.png "JS_HTMLVizProf_VizThru")  
  
  Użyj wykresu przepustowość wizualna do:  
  
- Określ ogólne obszary zainteresowania.  
  
- Wybierz określonego przedziału czasu do wyświetlenia na wykresie szczegółów osi czasu. Aby wybrać okres czasu, wybierz częścią wykresu, a następnie przeciągnij wskaźnik, aby dokonać wyboru.  
  
- Uzyskać bardziej szczegółowy widok w wybranym okresie, wybierając **powiększyć** przycisku.  
  
###  <a name="TimelineDetails"></a> Wyświetl szczegóły osi czasu  
 Wykres szczegóły osi czasu pojawi się w dolnym okienku Profiler czasu odpowiedzi interfejsu użytkownika. Zawiera sekwencyjne i hierarchiczne informacje o zdarzeniach, które są używane najwięcej czasu Procesora w wybranych okresach. Ten wykres może pomóc w określeniu przyczyny ich wyzwolenia konkretnego zdarzenia, a niektóre zdarzenia, jak zdarzenia mapuje do kodu źródłowego. Ten wykres pomaga określić czas wymagany do malowania aktualizacji visual na ekranie.  
  
 Na wykresie widać Praca wątku interfejsu użytkownika i na wątkach w tle, które może przyczynić się do wydłużenia aktualizacje programu visual. Wykres nie pokazuje pracy JavaScript JIT, asynchronicznego działanie procesora GPU, Praca wykonana poza procesem hosta (na przykład RuntimeBroker.exe i dwm.exe pracy) lub pracy dla obszarów środowiska wykonawczego Windows, które jeszcze nie został zinstrumentowany na potrzeby profilowania (np. We/Wy dysku).  
  
> [!TIP]
>  Gdy wystąpi zdarzenie w wątku tła, identyfikator wątku pojawia się w nawiasach obok nazwy zdarzenia.  
  
 Ten przykład pokazuje, jakie oś czasu wykresu szczegóły wygląda na to w przypadku odbiornik zdarzeń dla modelu DOM kliknij zdarzenie zostaje wybrany:  
  
 ![Oś czasu szczegóły wykresu](../profiling/media/js-htmlvizprof-timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Na tej ilustracji **spinAction** programu obsługi zdarzeń w **Nazwa zdarzenia** kolumna jest łącze, po wybraniu spowoduje przejście do narzędzia obsługi zdarzeń w kodzie źródłowym. W okienku po prawej stronie **funkcji wywołania zwrotnego** właściwość zawiera ten sam link do kodu źródłowego. Inne właściwości udostępniają informacje o zdarzeniu, takie jak skojarzonego elementu DOM w LICZBIE.  
  
 Jeśli wybierzesz część oś czasu użycia Procesora CPU i wykres przepustowość wizualna (kl. / s), wykres szczegóły osi czasu zawiera szczegółowe informacje dotyczące wybranego przedziału czasu.  
  
 Zdarzenia na wykresie szczegółów osi czasu są oznaczone kolorami do reprezentowania te same kategorie pracy, które są wyświetlane na wykresie użycia procesora CPU. Aby uzyskać więcej informacji na temat kategorii zdarzeń i określonych zdarzeń, zobacz [odwołanie do zdarzenia Profiler](#ProfilerEvents) w tym temacie.  
  
 Użyj wykresie szczegóły osi czasu, aby:  
  
-   Wyświetlanie godziny rozpoczęcia przybliżony czas trwania i zakończenia zdarzenia w widoku osi czasu i siatki. Oś czasu wykresu szczegółowe informacje można wyświetlić okresy od 30 milisekund do 30 sekund w zależności od stanu powiększenia widoku siatki. Aby uzyskać wartości czasu trwania:  
  
    -   Całkowity czas reprezentuje czas trwania zdarzenia, łącznie z elementami podrzędnymi zdarzeń. W widoku siatki ta wartość pojawia się jako pierwsza.  
  
    -   Wyłączny czas reprezentują czas trwania zdarzenia, nie wliczając dzieci zdarzeń. W widoku siatki ta wartość jest wyświetlana w nawiasach.  
  
-   Rozwiń zdarzenia w hierarchii, aby wyświetlić elementy podrzędne zdarzenia. Elementy podrzędne zdarzeń są inne zdarzenia, które są wywoływane przez zdarzenie nadrzędne. Na przykład zdarzenie modelu DOM może być detektorów zdarzeń, które są wyświetlane jako elementy podrzędne. Odbiornik zdarzeń mogą mieć inne zdarzenia, które są wynikiem, takich jak zdarzenia układu.  
  
-   Sortuj zdarzenia według start time (ustawienie domyślne) lub czas trwania. Użyj **sortować według** listę, aby wybrać metodę sortowania.  
  
-   Wyświetl szczegóły każdego zdarzenia w okienku szczegółów (w okienku po prawej stronie). Właściwości różnią się w zależności od określonego zdarzenia, jak pokazują powyższe przykłady:  
  
    -   Czasomierze, detektorów zdarzeń (zdarzenia DOM) i wywołania zwrotne ramek animacji **funkcji wywołania zwrotnego** właściwość zawiera również link do lokalizacji kodu źródłowego, wraz z nazwą zdarzenia funkcji obsługi lub wywołania zwrotnego.  
  
    -   Czasomierze, detektorów zdarzeń (zdarzenia DOM), układ zdarzenia i wywołania zwrotne ramek animacji oznaczone kolorami podsumowanie wybranego zdarzenia i jego elementy podrzędne są wyświetlane w **podsumowanie całkowitego czasu** sekcji (pierścień oznaczone kolorami). Każdy wycinek oznaczone kolorami obrazu reprezentuje typ zdarzenia. Etykietki narzędzi, podaj nazwę typu zdarzenia.  
  
    > [!TIP]
    >  Wykres szczegóły osi czasu i **podsumowanie całkowitego czasu** może pomóc w identyfikacji obszarów do optymalizacji. Jeśli jedno z tych widoków zawiera dużą liczbę małych zadań, zdarzenie może być kandydatem do optymalizacji. Na przykład aplikacja może być odświeżanie elementów DOM często skutkuje dużą liczbą układ i analizuje zdarzenia w formacie HTML. Dzięki temu można zoptymalizować wydajność, przetwarzanie wsadowe tych prac.  
  
###  <a name="FilterTimelineDetails"></a> Szczegóły osi czasu filtru  
 Wyświetl szczegóły osi czasu, aby konkretne zdarzenie można filtrować, wybierając **filtr, aby zdarzenia** z menu kontekstowego dla określonego zdarzenia. Po wybraniu tej opcji, widok osi czasu i siatki są ograniczone do wybranego zdarzenia. Wybór w wykres wykorzystania procesora CPU również zakresów do określonego zdarzenia.  
  
 ![Filtrowanie osi czasu, aby zdarzenie](../profiling/media/js-htmlvizprofiler-filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
###  <a name="FilterEvents"></a> Filtruj zdarzenia  
 Niektóre zdarzenia z wykresu szczegóły osi czasu szumu w danych lub usunąć dane, które nie jest on interesujący dla danego scenariusza wydajność można odfiltrować. Można filtrować według nazwy zdarzenia lub czas trwania zdarzenia lub przez określone filtry opisane w tym miejscu.  
  
 Aby odfiltrować dekodowanie obrazu, pobieranie spekulacyjne i zdarzenia GC, wyczyść **działania w tle** opcję ikonę filtru w dolnym okienku. Ponieważ te zdarzenia nie są bardzo informacje z możliwością działania, ich są domyślnie ukryte.  
  
 ![Filtrowanie zdarzeń na osi czasu](../profiling/media/js-htmlvizprofiler-event-filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 Aby odfiltrować zdarzeń żądania HTTP, wyczyść **ruch sieciowy** opcję ikonę filtru w dolnym okienku. Domyślnie te zdarzenia są wyświetlane na wykresie szczegółów osi czasu.  
  
 Aby odfiltrować aktywności wątku interfejsu użytkownika, wyczyść **działanie w interfejsie użytkownika** opcji.  
  
> [!TIP]
>  Usuń zaznaczenie tej opcji, a następnie wybierz opcję ruchu w sieci, aby zbadać problemy związane z opóźnieniem sieci.  
  
 Aby odfiltrować miary użytkownika, wyczyść **miary użytkownika** opcji. Miary użytkownika są zdarzenia najwyższego poziomu bez elementów podrzędnych.  
  
###  <a name="GroupFrames"></a> Grupowanie zdarzeń przez ramkę  
 Można grupować zdarzenia, które są wyświetlane w widoku Szczegóły osi czasu do poszczególnych klatek. Te zdarzenia ramki są zdarzenia generowane przez narzędzie i reprezentują kontenery zdarzenia najwyższego poziomu dla całą pracę wątku interfejsu użytkownika występuje między zdarzeniami malowania. Aby włączyć ten widok, wybierz **Grupuj zdarzenia najwyższego poziomu według klatek**.  
  
 ![Grupuj zdarzenia najwyższego poziomu według klatek](../profiling/media/js-htmlvizprofiler-frame-grouping-button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Zdarzenia w przypadku grupowania przez ramki, zdarzenia najwyższego poziomu w szczegółach osi czasu wyświetlania każdego reprezentują ramki.  
  
 ![Oś czasu zdarzeń, pogrupowane według ramki](../profiling/media/js-htmlvizprofiler-frame-grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
##  <a name="SaveSession"></a> Zapisywanie sesji diagnostycznej  
 W programie Visual Studio można zapisać sesji diagnostycznej informuj innych o zamknięciu kartę która ma skojarzony z sesją. Zapisane sesje można otworzyć ponownie w późniejszym czasie.  
  
##  <a name="ProfilerEvents"></a> Odwołanie do zdarzenia Profiler  
 Profiler zdarzenia są skategoryzowane i oznaczone kolorami w Profiler czasu odpowiedzi interfejsu użytkownika. Poniżej przedstawiono kategorie zdarzeń:  
  
- **Podczas ładowania.** Wskazuje czas spędzony na zasoby aplikacji podczas pobierania i analizowania HTML i CSS po pierwszym załadowaniu aplikacji. Może to obejmować żądania sieciowe.  
  
- **Obsługa skryptów.** Wskazuje czas poświęcony na analizowanie i uruchamianie kodu języka JavaScript. Obejmuje to zdarzenia modelu DOM, czasomierze, wyznaczanie wartości skryptu i pracy ramki animacji. Obejmuje ona zarówno kod użytkownika oraz kod biblioteki.  
  
- **GC.** Wskazuje czas spędzony na wyrzucanie elementów bezużytecznych.  
  
- **Ustawianie stylów.** Wskazuje czas spędzony analizy składni CSS i obliczanie prezentacji i układu elementu.  
  
- **Renderowanie.** Wskazuje czas spędzony na malowaniu ekranu.  
  
- **Dekodowanie obrazu.** Wskazuje czas spędzony na dekompresowaniu i dekodowaniu obrazów.  
  
  Dla skryptów i stylów kategorii Profiler czasu odpowiedzi interfejsu użytkownika może zawierać dane, które możesz działać na wykresie szczegółów osi czasu. Po zidentyfikowaniu zagadnienia dotyczące skryptów jako problem, można uruchomić program profilujący próbkowanie Procesora z Profiler czasu odpowiedzi interfejsu użytkownika. Alternatywnie można użyć programu Visual Studio profiler funkcji w celu uzyskania bardziej szczegółowych danych. Aby uzyskać więcej informacji, zobacz [danych analizowanie synchronizacja funkcji JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b).  
  
  W przypadku innych kategorii zdarzeń może być w stanie zidentyfikować efekty uboczne platformy, które powodują dodawanie funkcji do aplikacji, ale w takich przypadkach nie można rozwiązać problemy z wydajnością określonej za pomocą Profiler czasu odpowiedzi interfejsu użytkownika.  
  
  Ta tabela zawiera zdarzenia i ich opisy:  
  
|Zdarzenie|Kategoria zdarzenia|Występuje, gdy|  
|-----------|--------------------|-----------------|  
|Analizowanie arkusza CSS|Trwa ładowanie|Napotkano nową zawartość arkusza CSS, a nastąpiła próba przeanalizować zawartość arkusza CSS.|  
|Analizowanie kodu HTML|Trwa ładowanie|Napotkano nową zawartość HTML i przeanalizować zawartość w węzłach i wstawianie zawartości w drzewie DOM została podjęta próba.|  
|Żądanie HTTP|Trwa ładowanie|Zasób zdalny został znaleziony w modelu DOM lub utworzono XMLHttpRequest, które spowodowały wysłanie żądania HTTP.|  
|Pobieranie spekulacyjne|Trwa ładowanie|Zawartość HTML strony została wyszukiwane wymaganych zasobów, aby można było szybko zaplanować kolejne żądania HTTP dla zasobów.|  
|Funkcja wywołania zwrotnego ramki animacji|Wykonywanie skryptów|Przeglądarka został przejściem do innej ramki renderowania, a to wyzwalane funkcji wywołania zwrotnego dostarczane do aplikacji.|  
|Zdarzenie modelu DOM|Wykonywanie skryptów|Zdarzenie modelu DOM wystąpił i został wykonany.<br /><br /> `context` Właściwości zdarzenia DOM, takich jak `DOMContentLoaded` lub `click`, jest wyświetlany w nawiasach.|  
|Odbiornik zdarzeń|Wykonywanie skryptów|Odbiornik zdarzeń został wywoływane i wykonywane.|  
|Odbiornik zapytań o multimedia|Wykonywanie skryptów|Zarejestrowane zapytanie o multimedia zostało unieważnione, co spowodowało wykonanie skojarzonych z nim odbiorników.|  
|Obserwator mutacji|Wykonywanie skryptów|Co najmniej jeden należy zauważyć, że elementów DOM został zmodyfikowany, co spowodowało wykonanie wywołania zwrotnego skojarzonego z elementem MutationObserver.|  
|Wyznaczanie wartości skryptu|Wykonywanie skryptów|Nowy element skrypt został znaleziony w modelu DOM i była podejmowana próba analizy i uruchom skrypt.|  
|Czasomierz|Wykonywanie skryptów|Zaplanowany czasomierz zakończył odliczanie i pozwoliło to odnotować wykonywanie jej funkcji wywołania zwrotnego skojarzonego.|  
|Funkcja wywołania zwrotnego asynchronicznych środowiska wykonawczego Windows|Wykonywanie skryptów|Operacji asynchronicznej, która wyzwoliła `Promise` funkcji wywołania zwrotnego wykonał obiektu Windows Runtime.|  
|Zdarzenia środowiska uruchomieniowego Windows|Wykonywanie skryptów|Zdarzenie, które wystąpiły w obiekcie środowiska wykonawczego Windows wyzwolone zarejestrowane odbiornika.|  
|Wyrzucanie elementów bezużytecznych|GC|Tracony jest czas zbieranie pamięci obiektów, które były już używane.|  
|Obliczanie CSS|Ustawianie stylów|Wprowadzono zmiany w modelu DOM, który wymagany dla wszystkich elementów do ponownego obliczenia właściwości stylu.|  
|Układ|Ustawianie stylów|Wprowadzono zmiany w modelu DOM, wymaganego rozmiaru i/lub pozycji wszystkich elementów objętych do ponownego obliczenia.|  
|Malowanie|Renderowanie|Wprowadzono zmiany wizualne w modelu DOM i była podejmowana próba ponownego renderowania części strony.|  
|Warstwa renderowania|Renderowanie|Wprowadzono zmiany wizualne niezależnie renderowanych fragmentu modelu DOM (nazywana warstwą), a część strony do renderowania wymaganych zmian.|  
|Dekodowanie obrazu|Dekodowanie obrazu|Obraz został włączony w modelu DOM, a nastąpiła próba rozpakowania i dekodowanie obrazu z oryginalnego formatu do mapy bitowej.|  
|Klatka|Brak|Wprowadzono zmiany wizualne w modelu DOM, wszystkie objęte części strony aby być narysowany ponownie wymagane. Jest to zdarzenie generowane przez narzędzie używane do grupowania.|  
|Miara użytkownika|Brak|Scenariusz specyficzny dla aplikacji został zmierzony za `performance.measure` metody. Jest to zdarzenie generowane przez narzędzie używane do analizowania kodu.|  
  
##  <a name="Tips"></a> Dodatkowe informacje  
  
-   Obejrzyj [ten film wideo](http://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Build 2013 o Profiler czasu odpowiedzi interfejsu użytkownika.  
  
-   Przeczytaj wskazówki dotyczące wydajności dla aplikacji Windows Store utworzonych dla Windows przy użyciu języka JavaScript. Aby uzyskać więcej informacji, zobacz [wydajność — najlepsze rozwiązania dla aplikacji Windows Store przy użyciu języka JavaScript](http://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
-   Informacje na temat modelu wykonywania kodu jednowątkowego i wydajności, zobacz [wykonywanie kodu](http://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności aplikacji](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)



