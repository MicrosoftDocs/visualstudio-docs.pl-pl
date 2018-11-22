---
title: Wątki widoku w Wizualizatorze współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32a40553cd3f547dfa2b5297c898fabbd9664496
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281839"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Widok wątków w Wizualizatorze współbieżności

**Wątki** jest maksymalnie szczegółową i bogate widok w Wizualizatorze współbieżności. W **wątków** widoku można zidentyfikować, które wykonują wątki kodu podczas wykonywania segmentu i sprawdzić, czy wątki są wykonywanie lub blokowania z powodu synchronizacji, operacji We/Wy lub z innych powodów. **Wątki** Wyświetl raporty również profilować wykonywania drzewo stosu wywołań i odblokowywania wątków.

Gdy wykonują wątki Concurrency Visualizer służy do zbierania próbek. Gdy wątek zatrzymała wykonywanie, wizualizatora sprawdza, czy wszystkie zdarzenia przełączenie kontekstu systemu operacyjnego dla wątku. Przełączenia kontekstu może być fakt, że:  
  
- Wątek jest zablokowany na podstawowy synchronizacji.  
- Wygasa quantum wątku.  
- Wątek żąda blokowania We/Wy.  

Narzędzie CONCURRENCY Visualizer na działaniach kategoryzuje zdarzenia wątku i przełączenie kontekstu, a na koniec przeszukuje stosy wywołań wątków dla dobrze znanych interfejsów API, blokowania. Wyświetla kategorie wątku w aktywna Legenda w lewym dolnym w **wątków** widoku. W większości przypadków można zidentyfikować głównych przyczyn zdarzeń blokowania, sprawdzając stosy wywołań, które odnoszą się do przełączania kontekstu zdarzenia.

Jeśli nie zostanie odnaleziony odpowiednik stosu wywołań, Concurrency Visualizer używa powód oczekiwania, dostarczone przez [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Jednak [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategorii mogą opierać się na szczegółowo opisuje implementacja i mogą nie odzwierciedlać intencji użytkownika. Na przykład [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] raporty powód oczekiwania dotyczące blokowania na blokadzie natywnych zapisywania kieszeń czytnika jako operacji We/Wy, zamiast synchronizacji.  
  
**Wątki** widok również przedstawia zależności między wątkami. Na przykład można zidentyfikować wątku, który jest zablokowany na obiekt synchronizacji, można znaleźć wątku, który odblokował go. Stos wywołań odblokowywania wątku w momencie można sprawdzić po jej odblokowaniu jeden z nich.  

Możesz użyć **wątków** wyświetlania, aby:  

- Zidentyfikuj przyczyn interfejsu użytkownika (UI) aplikacji nie odpowiada podczas niektórych faz wykonywania.  
- Określ ilość czasu, który ma poświęcony blokowania synchronizacji, operacji We/Wy, błędów stron i inne zdarzenia.  
- Odkryj stopień zakłócenia wywoływane przez inne procesy, które są wykonywane w systemie.  
- Identyfikowanie problemów równoważenia obciążenia dla przetwarzania równoległego.  
- Znajdź przyczyny skalowalność nieoptymalne lub nie istnieje. Na przykład, dlaczego wydajność aplikacji równoległych nie poprawia dostępnych rdzeni bardziej logiczne.  
- Dowiedz się, stopień współbieżności w aplikacji, aby pomóc w przetwarzania równoległego.  
- Określenie zależności między wątków roboczych i krytyczne ścieżki wykonywania.  
  
## <a name="use-threads-view"></a>Użyj widoku wątków 

Aby uruchomić narzędzie Concurrency Visualizer, zaznacz **analizy** > **Concurrency Visualizer**, a następnie wybierz opcję, taką jak **uruchamianie nowego procesu**. 

Narzędzie CONCURRENCY Visualizer uruchamia aplikację i zbiera dane śledzenia, dopóki nie wybierzesz **Zatrzymaj Kolekcjonowanie**. Wizualizator następnie analizuje śledzenia i wyświetla wyniki na stronie raportu śledzenia. 

Wybierz **wątków** karty w lewej górnej w raporcie, aby otworzyć **wątków** widoku. 

![Widok wątków](../profiling/media/threadsviewnarrowing.png "widoku wątków")  
  
Wybierz odstępach czasu i wątki można uruchomić analizy wydajności.  
  
## <a name="timeline-analysis"></a>Analiza osi czasu  

W górnej części **wątków** widok jest osi czasu. Oś czasu aktywnością wszystkie wątki w procesie i wszystkie urządzenia dysku fizycznego na komputerze-hoście. Zdarzenia procesora GPU działania i znacznika jest również wyświetlana.  

Na osi czasu osi x to czas na osi y są oraz różnych kanałów:  
  
- Dwa kanały operacji We/Wy dla każdego dysku twardego systemu, jeden kanał dla odczytów i jeden dla zapisu.  
- Kanał dla każdego wątku w procesie.  
- W przypadku zdarzeń znaczników w śledzeniu kanały znacznika. Kanały znacznika początkowo wyświetlane w ramach kanałów wątków, które wygenerowany tych zdarzeń.  
- Kanały procesora GPU.  
  
Początkowo wątki są sortowane w kolejności, w którym są tworzone, dzięki czemu następuje wątku głównego aplikacji. Wybierz inną możliwością **sortować według** listę rozwijaną, aby posortować wątków przez innych kryteriów, takich jak **wykonywania**. 

Kolory osi czasu wskazują stan wątku w danym momencie. Zielony segmentów są wykonywane, czerwony segmentów zostaną zablokowane dla synchronizacji, żółty segmentów są przerywane i purpurowa segmentów są zaangażowane w We/Wy urządzenia. 

Powiększ, aby wyświetlić więcej szczegółów lub Pomniejsz do wyświetlania dłuższy interwał czasu. Wybierz segmentów punktów na wykresie, aby uzyskać szczegółowe informacje o kategorii, godziny, opóźnienia, rozpoczęcia i Stany stosu wywołań.  

Użyj osi czasu, aby sprawdzić saldo pracę pomiędzy wątki, które są zaangażowane w pętli równoległej lub współbieżnych zadań. Jeśli jeden wątek trwa dłużej niż inne, praca może być niezrównoważone. Dzięki rozłożeniu pracy bardziej równomiernie między wątków może zwiększyć wydajność aplikacji.  
  
Jeśli tylko jeden wątek jest wykonywanie w punkcie w czasie, aplikacji może nie być wykorzystanie pełnej współbieżności w systemie. Wykres osi czasu można użyć do sprawdzenia zależności między wątkami i Pokazuję tymczasowe relacje między blokowania i zablokowane wątki. Aby zmienić kolejność wątków, wybierz wątek, a następnie wybierz górę lub dół ikonę na pasku narzędzi. 

Można ukryć, wątki, które nie robią pracy lub są całkowicie zablokowane, ponieważ ich statystyki są zbędne i można clog — raporty. Ukryj wątki, wybierając ich nazw, a następnie wybierając **Ukryj wybrane wątki** lub **Ukryj wszystkie wątki z wyjątkiem wybranych** ikony na pasku narzędzi. Aby zidentyfikować wątków, aby ukryć, wybierz **na podsumowanie wątku** link w lewym dolnym rogu. Można ukryć wątków, które mają żadnych działań w **na podsumowanie wątku** wykresu. 

### <a name="thread-execution-details"></a>Szczegóły wykonywania wątków  
Aby uzyskać bardziej szczegółowe informacje dotyczące wykonywania segmentu, wybierz punkt na zielonym segmencie osi czasu. Narzędzie Concurrency Visualizer wyświetla czarny daszek powyżej wybranego punktu i pokazuje jego stos wywołań w **bieżącego** karty na dole. Możesz wybrać wiele punktów do tego segmentu wykonania.  
  
>[!NOTE]
>Narzędzie Concurrency Visualizer nie można rozpoznać zaznaczenia w segmencie wykonywania, jeśli czas trwania segmentu jest mniejszym niż jedna Milisekunda.  
  
Aby uzyskać profil wykonania dla wszystkich odkrywanie wątków w aktualnie wybranym zakresie czasu, wybierz **wykonywania** w legendzie w lewym dolnym rogu.  
  
### <a name="thread-blocking-details"></a>Blokuje wątek szczegóły  
Aby uzyskać informacje na temat konkretnego regionu na wątek, umieść kursor tego regionu na osi czasu, aby wyświetlić etykietkę narzędzia. Etykietka narzędzia zawiera informacje, takie jak kategorii, czas rozpoczęcia i opóźnienie. Wybierz region, aby wyświetlić stos wywołań w danym momencie w **bieżącego** karty na dole. W okienku zostaną wyświetlone również kategorii, opóźnienie, blokuje interfejsu API, jeśli istnieje, a odblokowanie wątku, jeśli taka istnieje. Sprawdzając stos wywołań, można określić podstawowej przyczyny blokuje wątek zdarzenia.  
  
Ścieżki wykonywania może mieć kilka zdarzeń blokujących. Aby zbadać je według kategorii blokowania i szybciej znaleźć obszarów problemów, zaznacz kategorię blokowania legendę po lewej stronie.  
  
### <a name="dependencies-between-threads"></a>Zależności między wątkami  
Narzędzie Concurrency Visualizer przedstawia zależności między wątkami, dzięki czemu można określić, co zablokowany wątek próbował wykonać i które z innego wątku włączony do wykonania. 

Aby ustalić, który wątek odblokowany inny wątek, zaznacz segment blokujący na osi czasu. Jeśli narzędzie Concurrency Visualizer można określić odblokowywanie wątków, rysuje linię między odblokowywanie wątków i wykonywanie segment, który następuje po segment blokujący. Wybierz **stos odblokowywania** karty w dolnym okienku, aby zobaczyć stos wywołań istotne.  
  
## <a name="profile-reports"></a>Profilu, raportów 
Poniżej oś czasu wykresu jest okienko z **raport profilu**, **bieżącego**, i **stos odblokowywania** raportu karty. Raporty są automatycznie aktualizowane wraz ze zmianą opcje osi czasu i wątków. Dla dużych śladów okienko raportów mogą być tymczasowo niedostępne, gdy aktualizacje są obliczane. 

### <a name="profile-report-tab"></a>Raport profilu 

**Raport profilu** ma dwa filtry:

- Aby odfiltrować wpisy drzewo wywołań nieco wykorzystania czasu, wpisz wartość filtru zakresu od 0 do 99 procent w **Noise redukcji przy** pola. Wartość domyślna to % 2. 
- Zaznacz, aby wyświetlić drzewa wywołań dla tylko Twój kod **tylko mój kod** pole wyboru. Aby wyświetlić wszystkie drzewa wywołań, wyczyść pole wyboru.  

**Raport profilu** karta zawiera raporty dla kategorii i łącza w legendzie. Aby wyświetlić raport, wybierz jeden z wpisów z lewej strony:  

- **Wykonanie**  
  **Wykonywania** raport zawiera podział czas potrzebny do aplikacji podczas wykonywania.  
  
  Aby znaleźć wiersza kodu, w którym jest czas wykonywania, rozwiń drzewo wywołań, a następnie w menu skrótów dla pozycji drzewo wywołań, wybierz **Wyświetl źródło** lub **widok wywołań witryn**. **Wyświetl źródło** lokalizuje wykonanego wiersza kodu. **Wyświetlanie wywołań witryn** lokalizuje wiersz kodu, który wywołał wykonanego wiersza. Jeśli tylko jeden wiersz witryny wywołania istnieje, jest wyróżniona swój kod. Jeśli wywołanie kilka witryn istnieje, wybierz ten, w oknie dialogowym, a następnie wybierz **przejdź do źródła**. Często jest najbardziej przydatne do lokalizowania strony wywołania, najbardziej wystąpień i/lub najwięcej czasu. Aby uzyskać więcej informacji, zobacz [raport profilu wykonania](../profiling/execution-profile-report.md).  
  
- **Synchronizacja**  
  **Synchronizacji** przedstawia wywołania, które są odpowiedzialne za bloki synchronizacji, wraz z łącznie blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas synchronizacji](../profiling/synchronization-time.md).  
  
- **OPERACJE WE/WY**  
  **Operacji We/Wy** przedstawia wywołania, które są odpowiedzialne za bloki operacji We/Wy, wraz z łącznie blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji We/Wy (Widok wątków)](../profiling/i-o-time-threads-view.md).  
  
- **Stan uśpienia**  
  **Uśpienia** przedstawia wywołania, które są odpowiedzialne za bloki uśpienia, wraz z łącznie blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).  
  
- **Zarządzanie pamięcią**  
  **Zarządzanie pamięcią** raport przedstawia wywołania, w których wystąpiła bloków zarządzania pamięci, wraz z łącznie blokuje razy każdego stosu wywołań. Te informacje służą do identyfikacji obszarów, które mają nadmierne problemy stronicowania lub wyrzucanie elementów z kolekcją.  Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).  
  
- **Wywłaszczania**  
  **Wywłaszczania** raport przedstawia, w którym procesy w systemie przerywane bieżącego procesu, a poszczególne wątki, które są zastępowane wątki w bieżącym procesie. Można użyć tych informacji do identyfikacji procesów i wątków, które są najbardziej odpowiedzialny za wywłaszczania. Aby uzyskać więcej informacji, zobacz [czas Wywłaszczania](../profiling/preemption-time.md).  
  
- **Przetwarzanie interfejsu użytkownika**  
  **Przetwarzania interfejsu użytkownika** przedstawia wywołania, które są odpowiedzialne za bloki przetwarzania interfejsu użytkownika, wraz z łącznie blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).  
  
- **Na podsumowanie wątku**  
  Wybierz **na podsumowanie wątku** do zawierają wykres przedstawiający stan wątków dla aktualnie wybranego okresu. Kolumny oznaczone kolorami, Pokaż łączny czas każdy wątek w uruchamiać, zablokowany, we/wy i inne stany. Wątki są oznaczone jako u dołu. Gdy możesz dostosować poziom powiększenia w wykres osi czasu, ten wykres jest automatycznie aktualizowany. 
  
  Niektóre poziomach powiększenia niektóre wątki mogą są wyświetlane na wykresie. W takim przypadku, wielokropek (**...** ) są wyświetlane po prawej stronie. Jeśli wątek, który ma nie zostanie wyświetlony, możesz ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [na raport z podsumowaniem wątku](../profiling/per-thread-summary-report.md).  
  
- **Operacje dyskowe**  
  Wybierz **operacje dyskowe** pokazanie procesy i wątki związane z We/Wy dysku dla bieżącego procesu, pliki, ich dotknięciu (np. biblioteki DLL są załadowane), liczbę bajtów odczytywane i inne informacje. Ten raport służy do oceny czasu uzyskiwania dostępu do plików w czasie wykonywania, szczególnie w przypadku, gdy proces wydaje się być I/O-powiązane z. Aby uzyskać więcej informacji, zobacz [raport dotyczący operacji na dysk](../profiling/disk-operations-report-threads-view.md).  
  
### <a name="current-tab"></a>Aktualna karta  
Ta karta przedstawia stos wywołań dla wybranego punktu w segmencie wątku na wykresie osi czasu. Stosy wywołań są usuwane, aby pokazać tylko te działania, które jest związane z aplikacją.  
  
### <a name="unblocking-stack-tab"></a>Odblokowywanie karty stosu 
Na karcie pokazywana, który wątek odblokowany zaznaczonych wątków i stos wywołań odblokowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)