---
title: Widok wątków (wydajność równoległa) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821989"
---
# <a name="threads-view-parallel-performance"></a>Widok wątków (Parallel Performance)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wątków to najbardziej szczegółowy i wzbogacony widok funkcji w wizualizatorze współbieżności. Za pomocą tego widoku można określić, czy wątki są wykonywane czy blokowane z powodu synchronizacji, we/wy lub z innego powodu.  
  
 Podczas analizy profilu, Wizualizator współbieżności bada wszystkie zdarzenia dotyczące przełącznika kontekstu systemu operacyjnego dla każdego wątku aplikacji. Przełączenia kontekstu mogą wystąpić z wielu powodów, takich jak następujące:  
  
- Wątek jest blokowany dla elementu podstawowego synchronizacji.  
  
- Element Quantum dla wątku wygasa.  
  
- Wątek sprawia, że blokowane żądanie we/wy.  
  
  Widok wątków przypisuje kategorię do każdego przełączenia kontekstu, gdy wątek przestanie działać. Kategorie są wyświetlane w legendzie w lewej dolnej części widoku. Wizualizator współbieżności klasyfikuje zdarzenia przełączenia kontekstu, wyszukując stos wywołań wątku dla dobrze znanych, blokowanych interfejsów API. Jeśli nie ma dopasowania stosu wywołań, używany jest powód oczekiwania podany przez [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] . Jednak [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] Kategoria może opierać się na szczegółach implementacji i może nie odzwierciedlać intencji użytkownika. Na przykład program [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] raportuje przyczynę oczekiwania na zablokowanie natywnej, cienkiej blokady czytnika i/O zamiast synchronizacji. W większości przypadków można zidentyfikować główną przyczynę zdarzenia blokującego, badając stosy wywołań odpowiadające zdarzeniom przełączania kontekstu.  
  
  Widok wątki zawiera również zależności między wątkami. Na przykład, jeśli określisz wątek, który jest zablokowany w obiekcie synchronizacji, można wyszukać wątek, który go odblokował, i można sprawdzić działanie w stosie wywołań dla tego wątku w momencie odblokowania go.  
  
  Gdy wątki są wykonywane, Wizualizator współbieżności zbiera próbki. W widoku wątki można analizować, który kod jest wykonywany przez jeden lub więcej wątków w ramach segmentu wykonywania. Możesz również przejrzeć raporty dotyczące blokowania i raporty, które profilują wykonywanie w drzewie wywołań.  
  
## <a name="usage"></a>Użycie  
 Oto kilka sposobów korzystania z widoku wątki:  
  
- Określ przyczyny braku odpowiedzi interfejsu użytkownika w niektórych fazach wykonywania.  
  
- Określ czas, w którym wykorzystano blokowanie synchronizacji, operacji we/wy, błędów stron i innych zdarzeń.  
  
- Określ stopień zakłóceń między innymi procesami, które są wykonywane w systemie.  
  
- Identyfikuj problemy z równoważeniem obciążenia na potrzeby wykonywania równoległego.  
  
- Zidentyfikuj przyczyny skalowalności, która jest optymalna lub nieistniejąca (na przykład Dlaczego wydajność aplikacji równoległej nie poprawi się, gdy są dostępne więcej rdzeni logicznych).  
  
- Poznaj stopień współbieżności w aplikacji, aby pomóc w przetwarzanie równoległe.  
  
- Zrozumienie zależności między wątkami roboczymi i krytycznymi ścieżkami wykonywania.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Badanie określonych przedziałów czasu i wątków  
 Widok wątki pokazuje oś czasu. Możesz powiększać i kadrować na osi czasu w celu sprawdzenia określonych interwałów i wątków aplikacji. Na osi x jest czas, a na osi y jest kilka kanałów:  
  
- Dwa kanały we/wy dla każdego dysku w systemie, jeden kanał do odczytu i jeden dla operacji zapisu.  
  
- Kanał dla każdego wątku w procesie.  
  
- Kanały znacznika, jeśli istnieją zdarzenia znacznika w śladzie. Kanały znaczników początkowo pojawiają się w obszarze kanałów wątku, które wygenerowały te zdarzenia.  
  
- Kanały procesora GPU.  
  
  Oto ilustracja przedstawiająca widok wątki:  
  
  ![Widok wątków](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  Widok wątków  
  
  Początkowo wątki są sortowane w kolejności, w której zostały utworzone, tak aby wątek głównej aplikacji był pierwszy. Możesz użyć opcji sortowania w lewym górnym rogu widoku, aby posortować wątki według innego kryterium (na przykład przez większość wykonanych zadań wykonywania).  
  
  Można ukryć wątki, które nie wykonują pracy, wybierając ich nazwy w kolumnie po lewej stronie, a następnie wybierając przycisk **Ukryj wybrane wątki** na pasku narzędzi. Zalecamy ukrycie wątków, które są całkowicie zablokowane, ponieważ ich statystyki są nieistotne i mogą CLOG raporty.  
  
  Aby określić dodatkowe wątki do ukrycia, w aktywnej legendzie wybierz Raport **podsumowujący wątek** na karcie **raport o profilu** . Spowoduje to wyświetlenie wykresu podziału wykonania, który pokazuje stan wątków dla aktualnie wybranego interwału czasu. Na pewnych poziomach powiększenia niektóre wątki mogą nie być wyświetlane. W takim przypadku elipsy są wyświetlane po prawej stronie.  
  
  Po wybraniu interwału i niektórych wątków można rozpocząć analizę wydajności.  
  
## <a name="analysis-tools"></a>Narzędzia do analizy  
 W tej sekcji opisano raporty i inne narzędzia do analizy.  
  
### <a name="thread-blocking-details"></a>Szczegóły blokowania wątku  
 Aby uzyskać informacje o zdarzeniu blokującym w określonym regionie wątku, umieść wskaźnik w tym regionie, aby wyświetlić etykietkę narzędzia. Zawiera informacje, takie jak kategoria, czas rozpoczęcia regionu, czas blokowania i blokowy interfejs API, jeśli istnieje. W przypadku wybrania regionu blokującego w dolnym okienku zostanie wyświetlony stos, a razem z tymi samymi informacjami, które są wyświetlane w etykietce narzędzia. Badając stos wywołań, można określić podstawową przyczynę zdarzenia blokowania wątku. Dodatkowe informacje o procesach i wątkach można znaleźć, wybierając segment i sprawdzając bieżącą kartę.  
  
 Ścieżka wykonywania może mieć wiele zdarzeń blokowania. Można je sprawdzić przez zablokowanie kategorii, dzięki czemu można szybciej znaleźć obszary problemów. Po lewej stronie wybierz jedną z kategorii blokowania.  
  
### <a name="dependencies-between-threads"></a>Zależności między wątkami  
 Wizualizator współbieżności może pokazać zależności między wątkami w procesie, aby można było określić, co zablokowany wątek próbował wykonać i dowiedzieć się, jakie inne wątki obsługują do wykonania. Aby określić, który wątek odblokował inny wątek, wybierz odpowiedni segment blokujący. Jeśli Wizualizator współbieżności może określić wątek odblokowywania, rysuje wiersz między wątkiem odblokowywania i segmentem wykonywania, który następuje po segmencie bloku. Ponadto na karcie **odblokowywanie stosu** są wyświetlane odpowiednie stosy wywołań.  
  
### <a name="thread-execution-details"></a>Szczegóły wykonania wątku  
 Na wykresie osi czasu wątku, zielone segmenty są wyświetlane podczas wykonywania kodu. Możesz uzyskać bardziej szczegółowe informacje na temat segmentu wykonania.  
  
 Po wybraniu punktu w segmencie wykonywania, Wizualizator współbieżności szuka tego punktu w czasie na odpowiednim stosie wywołań, a następnie wyświetla czarny karetkę nad wybranym punktem w segmencie wykonywania i wyświetla sam stos wywołań na karcie **bieżącego stosu** . Można wybrać wiele punktów w segmencie wykonywania.  
  
> [!NOTE]
> Wizualizator współbieżności może nie być w stanie rozpoznać zaznaczenia w segmencie wykonywania. Zwykle zdarza się to, gdy czas trwania segmentu jest krótszy niż jedna milisekunda.  
  
 Aby uzyskać profil wykonywania dla wszystkich włączonych (nieukrytych) wątków w aktualnie wybranym zakresie czasu, wybierz przycisk **wykonywania** w aktywnej legendzie.  
  
### <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu przedstawia aktywność wszystkich wątków w procesie i wszystkich urządzeń fizycznych na komputerze-hoście. Wyświetla również zdarzenia dotyczące aktywności procesora GPU i znaczników.  Możesz powiększyć widok, aby wyświetlić bardziej szczegółowe informacje, aby wyświetlić dłuższy interwał czasu. Możesz również wybrać punkty na grafie, aby uzyskać szczegółowe informacje o kategoriach, godzinach początkowych, czasach trwania i Stanach stosu wywołań.  
  
 Na wykresie osi czasu kolor wskazuje stan wątku w danym momencie. Na przykład, zielone segmenty zostały wykonane, czerwona segmenty zostały zablokowane do synchronizacji, żółte segmenty zostały zastępujące, a purpurowe segmenty zostały wykonane w ramach operacji we/wy na urządzeniu. Możesz użyć tego widoku, aby sprawdzić balans pracy między wątkami, które są uwzględnione w pętli równoległej lub w zadaniach współbieżnych. Jeśli wątek trwa dłużej niż inne, może to oznaczać, że działanie nie jest zrównoważone. Za pomocą tych informacji można poprawić wydajność programu Dzięki rozproszeniu pracy bardziej równomiernie między wątki.  
  
 Jeśli tylko jeden wątek jest zielony (wykonywany) w danym momencie, aplikacja może nie być w pełni wykorzystywać współbieżności w systemie. Wykres osi czasu służy do badania zależności między wątkami i relacjami czasowymi między blokowaniem i zablokowanymi wątkami. Aby zmienić rozmieszczenie wątków, zaznacz wątek, a następnie na pasku narzędzi wybierz przycisk w górę lub w dół. Aby ukryć wątki, zaznacz je, a następnie wybierz przycisk **Ukryj wątki** .  
  
### <a name="profile-reports"></a>Raporty profilowe  
 Poniżej wykresu osi czasu jest profil osi czasu oraz okienko z kartami dla różnych raportów. Raporty są automatycznie aktualizowane podczas zmiany widoku wątków. W przypadku dużych śladów okienko raporty może być niedostępne podczas obliczania aktualizacji. Każdy raport ma dwa ustawienia filtrowania: redukcja szumu i Tylko mój kod. Użyj redukcji szumu, aby odfiltrować wpisy drzewa wywołań, gdy jest czasochłonny niewielki czas. Domyślna wartość filtru to 2 procent, ale można ją dostosować od 0% do 99%. Aby wyświetlić tylko drzewo wywołań dla kodu, zaznacz pole wyboru **tylko mój kod** . Aby wyświetlić wszystkie drzewa wywołań, wyczyść je.  
  
#### <a name="profile-report"></a>Raport profilu  
 Na tej karcie są wyświetlane raporty, które odpowiadają wpisom w aktywnej legendzie. Aby wyświetlić raport, wybierz jeden z wpisów.  
  
#### <a name="current-stack"></a>Bieżący stos  
 Na tej karcie jest wyświetlany stos wywołań dla wybranego punktu w segmencie wątku na wykresie osi czasu. Stosy wywołań są przycinane do wyświetlania tylko działań związanych z programem.  
  
#### <a name="unblocking-stack"></a>Stos odblokowań  
 Aby zobaczyć, który wątek odblokował wybrany wątek, i w jakim wierszu kodu wybierz kartę **Odblokuj stos** .  
  
#### <a name="execution"></a>Wykonanie  
 Raport wykonywania pokazuje podział czasu, przez który aplikacja wykorzystała z wykonywania.  
  
 Aby znaleźć wiersz kodu, w którym jest poświęcony czas wykonywania, rozwiń drzewo wywołań, a następnie w menu skrótów dla wpisu drzewa wywołań wybierz polecenie **Wyświetl źródło** lub **Wyświetl Lokacje wywołań**. **Widok źródło** lokalizuje wykonany wiersz kodu. **Wyświetl Lokacje wywołań** lokalizuje wiersz kodu, który został wywołany przez wykonywany wiersz kodu. Jeśli istnieje tylko jedna lokacja wywołania, jego wiersz kodu jest wyróżniony. Jeśli istnieje wiele witryn wywołań, można wybrać odpowiedni w wyświetlonym oknie dialogowym, a następnie wybrać przycisk **Przejdź do źródła** , aby wyróżnić kod lokacji wywołania. Często jest to najbardziej przydatne do lokalizowania lokacji wywołań, która ma najwięcej wystąpień, w większości przypadków lub obu. Aby uzyskać więcej informacji, zobacz [raport profil wykonywania](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronizacja  
 Raport synchronizacji przedstawia wywołania, które są odpowiedzialne za bloki synchronizacji, oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [godzina synchronizacji](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>WE/WY  
 Raport we/wy przedstawia wywołania, które są odpowiedzialne za bloki we/wy oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji we/wy (Widok wątków)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Uśpij  
 Raport uśpienia zawiera wywołania, które są odpowiedzialne za bloki uśpienia oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Zarządzanie pamięcią  
 Raport zarządzanie pamięcią pokazuje wywołania, w których wystąpiły bloki zarządzania pamięcią, oraz łączny czas blokowania dla każdego stosu wywołań. Za pomocą tych informacji można identyfikować obszary, które mają nadmierne problemy z stronicowaniem lub odzyskiwaniem pamięci.  Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Wywłaszczania  
 Raport przeniesień przedstawia wystąpienia, w których procesy w systemie zastępują bieżący proces i poszczególne wątki, które zastąpiły wątki w bieżącym procesie. Te informacje służą do identyfikowania procesów i wątków, które są najbardziej odpowiedzialne za przeznaczenie. Aby uzyskać więcej informacji, zobacz [czas zastępujący](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika  
 Raport przetwarzania interfejsu użytkownika przedstawia wywołania, które są odpowiedzialne za bloki przetwarzania interfejsu użytkownika oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Na podsumowanie wątku  
 Na tej karcie jest wyświetlany widok kolumny kodowany kolorem łącznego czasu, przez który każdy wątek spędza w przebiegu, zablokowane, we/wy i innych Stanach. Kolumny są oznaczone etykietami u dołu. Po dostosowaniu poziomu powiększenia na wykresie osi czasu ta karta jest automatycznie aktualizowana. Na pewnych poziomach powiększenia niektóre wątki mogą nie być wyświetlane. W takim przypadku elipsy są wyświetlane po prawej stronie. Jeśli żądany wątek nie jest wyświetlany, można ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [raport podsumowujący wątek](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operacje na dyskach  
 Na tej karcie przedstawiono, które procesy i wątki dotyczyły operacji we/wy dysku w bieżącym procesie, które pliki zostały naruszone (na przykład załadowane biblioteki dll), ile bajtów zostało odczytanych i innych informacji. Za pomocą tego raportu można oszacować czas spędzony na uzyskiwaniu dostępu do plików podczas wykonywania, szczególnie w przypadku, gdy proces wydaje się być powiązany we/wy. Aby uzyskać więcej informacji, zobacz [raport operacji dyskowych](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
