---
title: Wątki widok (Parallel Performance) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d685dc39f5e07840a5995f7fe67988840c3f50a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441655"
---
# <a name="threads-view-parallel-performance"></a>Widok wątków (Parallel Performance)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wątków jest najbardziej szczegółowy i bogate widoku w Wizualizatorze współbieżności. Korzystając z tego widoku, można ustalić, czy wątki są wykonywanie lub blokowania z powodu synchronizacji, operacji We/Wy lub innego powodu.  
  
 Podczas analizy profilu Concurrency Visualizer sprawdza, czy wszystkie zdarzenia przełączenie kontekstu systemu operacyjnego dla każdego wątku aplikacji. Przełączeń kontekstu może wystąpić z wielu powodów, takich jak te:  
  
- Wątek jest zablokowany na podstawowy synchronizacji.  
  
- Wygasa quantum wątku.  
  
- Wątek żąda blokowania We/Wy.  
  
  Widok wątków przypisuje kategorię dla każdego przełącznika kontekstu po zatrzymaniu wątek wykonywania. Kategorie są wyświetlane w legendzie w lewej dolnej części widoku. Narzędzie Concurrency Visualizer na działaniach kategoryzuje zdarzenia przełączenie kontekstu przez wyszukiwanie dobrze znanych interfejsów API w blokowania stos wywołań wątku. Jeśli nie zostanie odnaleziony odpowiednik stosu wywołań powód oczekiwania, które są dostarczane przez [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] jest używany. Jednak [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] kategorii mogą opierać się na szczegółowo opisuje implementacja i mogą nie odzwierciedlać intencji użytkownika. Na przykład [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] raporty powód oczekiwania dotyczące blokowania na blokadzie natywnych zapisywania kieszeń czytnika jako operacji We/Wy, zamiast synchronizacji. W większości przypadków można zidentyfikować głównych przyczyn zdarzeń blokowania, sprawdzając stosy wywołań, które odnoszą się do przełączania kontekstu zdarzenia.  
  
  Widok wątki pokazuje również zależności pomiędzy wątkami. Na przykład po zidentyfikowaniu wątek, który jest zablokowany na obiekt synchronizacji, można wyszukać wątku, który odblokował go, a po jej odblokowaniu jeden z nich, można sprawdzić działanie w stosie wywołań dla tego wątku w punkcie.  
  
  Wykonywaniem wątków Concurrency Visualizer służy do zbierania próbek. W widoku wątków można analizować, której kod jest wykonywany przez jeden lub więcej wątków podczas segmentu wykonania. Można także sprawdzić blokowania raporty i raporty, które profil wykonania drzewo stosu wywołań.  
  
## <a name="usage"></a>Użycie  
 Oto kilka sposobów, że można użyć widoku wątków:  
  
- Zidentyfikuj powodów dlaczego interfejs użytkownika (UI) aplikacji nie odpowiada podczas niektórych faz wykonywania.  
  
- Określ ilość czasu, który ma poświęcony blokowania synchronizacji, operacji We/Wy, błędów stron i inne zdarzenia.  
  
- Określ stopień zakłócenia wywoływane przez inne procesy, które są wykonywane w systemie.  
  
- Identyfikowanie problemów równoważenia obciążenia dla przetwarzania równoległego.  
  
- Określ powody do skalowania, która jest nieoptymalne lub nie istnieje (na przykład, dlaczego wydajność aplikacji równoległych nie poprawia, gdy będzie dostępnych rdzeni bardziej logiczny).  
  
- Dowiedz się, stopień współbieżności w aplikacji, aby pomóc w przetwarzania równoległego.  
  
- Poznanie zależności pomiędzy wątki robocze i krytyczne ścieżki wykonywania.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Badanie w określonych odstępach czasu i wątki  
 Widok wątki pokazuje oś czasu. Możesz powiększać i przesuń w osi czasu, aby sprawdzić w określonych odstępach czasu i wątki aplikacji. Na osi x jest czas się na osi y różnych kanałów:  
  
- Dwa kanały operacji We/Wy dla każdego dysku twardego systemu, jeden kanał dla odczytów i jeden dla zapisu.  
  
- Kanał dla każdego wątku w procesie.  
  
- W przypadku zdarzeń znaczników w śledzeniu kanały znacznika. Kanały znacznika początkowo wyświetlane w ramach kanałów wątków, które wygenerowany tych zdarzeń.  
  
- Kanały procesora GPU.  
  
  Oto ilustrację Widok wątków:  
  
  ![Widok wątków](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  Widok wątków  
  
  Początkowo wątki są sortowane w kolejności, w którym są tworzone tak, aby następuje wątku głównego aplikacji. Opcja sortowania w lewym górnym rogu widoku sortowania wątki według innego kryterium (np. przez większość wykonywania pracy wykonanej).  
  
  Można ukryć, wątki, które nie wykonują pracę, wybierając ich nazwy w kolumnie po lewej stronie, a następnie wybierając **Ukryj wybrane wątki** przycisk na pasku narzędzi. Firma Microsoft zaleca ukrycie wątki, które są całkowicie zablokowane, ponieważ ich statystyki są zbędne i można clog — raporty.  
  
  Aby zidentyfikować dodatkowe wątki, aby ukryć w legendzie active wybierz **na podsumowanie wątku** sporządzić raport na temat **raport profilu** kartę. Spowoduje to wyświetlenie wykres podziału wykonywania, na którym pokazuje stan wątków dla aktualnie wybranego okresu. W niektórych poziomami powiększenia niektóre wątki mogą nie być wyświetlane. W takiej sytuacji wielokropek są wyświetlane po prawej stronie.  
  
  Po wybraniu interwału czasu i wątków w nim można uruchomić analizy wydajności.  
  
## <a name="analysis-tools"></a>Narzędzia do analizy  
 W tej sekcji opisano, raportów i innych narzędzi do analizy.  
  
### <a name="thread-blocking-details"></a>Blokuje wątek szczegóły  
 Aby uzyskać informacje o zdarzeniu blokowania w danym regionie w wątku, umieść wskaźnik na ten region, aby wyświetlić etykietkę narzędzia. Zawiera on informacje, takie jak kategorii, region, czas rozpoczęcia, czas blokowania i blokowania interfejsu API, jeśli taka istnieje. Jeśli wybierzesz opcję blokowania region, stosu w danym momencie jest wyświetlany w dolnym okienku wraz z tych samych informacji, który jest wyświetlany w etykietce narzędzia. Sprawdzając stos wywołań, należy określić główną przyczynę wysokiej skuteczności wydarzeniu blokowania wątku. Dodatkowych procesów i informacji o wątku można znaleźć, wybierając segmentu i badanie bieżącej karty.  
  
 Ścieżką wykonywania może mieć wiele zdarzeń blokujących. Można sprawdzić je według kategorii blokowania, więc, że możesz szybciej znaleźć obszarów problemów. Wystarczy wybrać jedną z kategorii blokowania w legendzie po lewej stronie.  
  
### <a name="dependencies-between-threads"></a>Zależności między wątkami  
 Narzędzie Concurrency Visualizer można wyświetlić zależności między wątkami w procesie, aby określić, co zablokowany wątek próbował wykonać i Dowiedz się, jakie inne wątku włączony do wykonania. Aby ustalić, który wątek odblokowany inny wątek, wybierz odpowiednie segment blokujący. Jeśli narzędzie Concurrency Visualizer można określić odblokowywanie wątków, rysuje linię między odblokowywanie wątków i wykonywanie segment, który następuje po segment blokujący. Ponadto **stosu Unblocking** karta przedstawia stos wywołań istotne.  
  
### <a name="thread-execution-details"></a>Szczegóły wykonywania wątków  
 Wykres osi czasu w wątku zielony segmentów pokazują, gdy był wykonywany kod. Możesz uzyskać bardziej szczegółowe informacje o segmentu wykonania.  
  
 Po wybraniu punktu w segmencie wykonywania Concurrency Visualizer szuka tego punktu w czasie w stosie wywołań odpowiednie wyświetla czarny daszek powyżej wybranym punkcie w segmencie wykonywania i przedstawia stos wywołań, sam na  **Bieżący stos** kartę. Możesz wybrać wiele punktów do tego segmentu wykonania.  
  
> [!NOTE]
> Narzędzie Concurrency Visualizer nie można rozpoznać zaznaczenia w segmencie wykonywania. Zwykle dzieje się po czas trwania segmentu mniejszym niż jedna Milisekunda.  
  
 Aby uzyskać profil wykonania wszystkie włączone (odkrywanie) wątków w aktualnie wybranym zakresie czasu, wybierz **wykonywania** przycisk aktywna Legenda.  
  
### <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu aktywnością wszystkie wątki w procesie i wszystkie urządzenia dysku fizycznego na komputerze-hoście. Zdarzenia procesora GPU działania i znacznika jest również wyświetlana.  Można powiększyć, aby wyświetlić więcej szczegółów lub poziomie w celu wyświetlenia dłuższy interwał czasu. Możesz również wybrać punktów na wykresie, aby uzyskać szczegółowe informacje o kategorii, godziny rozpoczęcia, czas trwania i Stany stosu wywołań.  
  
 Na wykresie oś czasu kolor, który wskazuje stan wątku w danym momencie. Na przykład wykonywały segmentów zielony, czerwony segmentów zostały zablokowane na synchronizacji, żółty segmentów były przerywane i purpurowa segmenty nie prowadzą We/Wy urządzenia. Ten widok służy do sprawdzenia równowagi między wątkami, które są zaangażowane w pętli równoległej lub współbieżnych zadań. Jeśli wątek trwa dłużej niż inne, praca może być niezrównoważone. Aby zwiększyć wydajność programu dzięki rozłożeniu pracy bardziej równomiernie między wątki, można użyć tych informacji.  
  
 Jeśli tylko jeden wątek jest zielony, (wykonywana) w punkcie w czasie, aplikacja może nie być zalet pełną współbieżność w systemie. Wykres osi czasu można użyć do sprawdzenia zależności między wątkami i Pokazuję tymczasowe relacje między blokowania i zablokowane wątki. Aby zmienić kolejność wątków, wybierz wątku, a następnie na pasku narzędzi wybierz pozycję w górę lub dół. Aby ukryć wątków, zaznacz je, a następnie wybierz **Ukryj wątki** przycisku.  
  
### <a name="profile-reports"></a>Profilu, raportów  
 Poniżej oś czasu wykresu jest profil osi czasu i okienko które zawiera karty dla różnych raportów. Raporty są automatycznie aktualizowane wraz ze zmianą Widok wątków. Dla dużych śladów okienko raportów mogą być niedostępne, gdy aktualizacje są obliczane. Każdy raport zawiera dwa dopasowania filtru: noise redukcję i tylko mój kod. Użyj redukcji szumu, aby odfiltrować wpisy drzewo wywołań gdzie odbywa się trochę czasu. Domyślna wartość filtru jest % 2, ale można dostosować od 0 do 99 procent. Zaznacz, aby wyświetlić tylko drzewo wywołań dla kodu **tylko mój kod** pole wyboru. Aby wyświetlić wszystkie drzewa wywołań, usuń zaznaczenie.  
  
#### <a name="profile-report"></a>Raport profilu  
 Ta karta przedstawia raporty, które odnoszą się do wpisów w aktywna Legenda. Aby wyświetlić raport, wybierz jeden z wpisów.  
  
#### <a name="current-stack"></a>Bieżący stos  
 Ta karta przedstawia stos wywołań dla wybranego punktu w segmencie wątku na wykresie osi czasu. Stosy wywołań są usuwane, aby pokazać tylko te działania, które jest związane z programu.  
  
#### <a name="unblocking-stack"></a>Stos odblokowań  
 Aby zobaczyć, który wątek odblokowany zaznaczonych wątków, a na wiersz kodu, wybierz **stosu Unblocking** kartę.  
  
#### <a name="execution"></a>Wykonanie  
 Wykonanie przedstawia podział czas potrzebny do aplikacji podczas wykonywania.  
  
 Aby znaleźć wiersza kodu, w którym jest czas wykonywania, rozwiń drzewo wywołań, a następnie w menu skrótów dla pozycji drzewo wywołań, wybierz **Wyświetl źródło** lub **widok wywołań witryn**. **Wyświetl źródło** lokalizuje wykonanego wiersza kodu. **Wyświetlanie wywołań witryn** lokalizuje wiersz kodu, który wywołał wykonanego wiersza kodu. Jeśli tylko jedna lokacja wywołanie istnieje, jest wyróżniona jego wiersz kodu. Jeśli istnieje wiele wywołań, można wybrać w oknie dialogowym, który pojawia się, a następnie wybierz żądaną **przejdź do źródła** przycisk, aby wyróżnić wywołanie kodu lokacji. Często jest najbardziej przydatne do lokalizowania strony wywołania, najbardziej wystąpień i/lub najwięcej czasu. Aby uzyskać więcej informacji, zobacz [raport profilu wykonania](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronizacja  
 Synchronizacja przedstawia wywołania, które są odpowiedzialne za bloki synchronizacji, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas synchronizacji](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>WE/WY  
 Operacje We/Wy przedstawia wywołania, które są odpowiedzialne za bloki operacji We/Wy, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji We/Wy (Widok wątków)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Stan uśpienia  
 Uśpienie przedstawia wywołania, które są odpowiedzialne za bloki uśpienia, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Zarządzanie pamięcią  
 Raport zarządzania pamięci Wyświetla wywołania, gdy bloków zarządzania pamięci wystąpiły, wraz z agregacji blokuje razy każdego stosu wywołań. Można użyć tych informacji do identyfikacji obszarów, które mają nadmierne problemy stronicowania lub wyrzucanie elementów z kolekcją.  Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Wywłaszczania  
 Raport Wywłaszczania zawiera wystąpienia, gdzie procesy w systemie przerywane bieżący proces i poszczególne wątki, które zastąpione wątki w bieżącym procesie. Można użyć tych informacji do identyfikacji procesów i wątków, które są najbardziej odpowiedzialny za wywłaszczania. Aby uzyskać więcej informacji, zobacz [czas Wywłaszczania](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika  
 Raport przetwarzania interfejsu użytkownika zawiera wywołania, które są odpowiedzialne za interfejs użytkownika, przetwarzanie bloki, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Na podsumowanie wątku  
 Ta karta przedstawia widok kolumna oznaczona kolorami, łączny czas, czy każdy wątek w procesie, zablokowany, we/wy i inne stany. Kolumny są oznaczone jako u dołu. Podczas dostosowywania na poziomie powiększenie w wykres osi czasu na tej karcie jest aktualizowane automatycznie. W niektórych poziomami powiększenia niektóre wątki mogą nie być wyświetlane. W takiej sytuacji wielokropek są wyświetlane po prawej stronie. Jeśli wątek, który ma nie zostanie wyświetlony, możesz ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [na wątku raport z podsumowaniem](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operacje dyskowe  
 Ta karta przedstawia procesy i wątki były związane z We/Wy dysku w imieniu bieżącego procesu, które pliki są dotknięciu (np. biblioteki dll, które zostały załadowane), liczbę bajtów zostały odczytane oraz inne informacje. Ten raport służy do oceny czasu spędzonego w dostęp do plików w czasie wykonywania, szczególnie w przypadku, gdy proces wydaje się być powiązany we/wy. Aby uzyskać więcej informacji, zobacz [raport operacji dyskowych](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
