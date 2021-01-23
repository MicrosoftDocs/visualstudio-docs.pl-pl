---
title: Widok wątków w wizualizatorze współbieżności | Microsoft Docs
description: Sprawdź, czy w widoku wątki można określić, które wątki wykonuje kod w czasie wykonywania.
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619e76b3db67314119782ebc3010465ac7fa622f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722727"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Widok wątków w wizualizatorze współbieżności

Widok **wątków** to najbardziej szczegółowy i wzbogacony widok funkcji w wizualizatorze współbieżności. W widoku **wątki** można zidentyfikować wątki wykonujące kod podczas segmentów wykonywania i analizować, czy wątki są wykonywane lub blokowane z powodu synchronizacji, we/wy lub z innych przyczyn. **Wątki** wyświetlają również profile profilu wywołania i odblokowywania na stosie.

Gdy wątki są wykonywane, Wizualizator współbieżności zbiera próbki. Po zatrzymaniu wątku wizualizator analizuje wszystkie zdarzenia dotyczące przełącznika kontekstu systemu operacyjnego dla wątku. Mogą wystąpić przełączenia kontekstu, ponieważ:

- Wątek jest blokowany dla elementu podstawowego synchronizacji.
- Element Quantum dla wątku wygasa.
- Wątek sprawia, że blokowane żądanie we/wy.

Wizualizator współbieżności klasyfikuje zdarzenia wątku i przełączenia kontekstu, a następnie wyszukuje stosy wywołań wątków dla dobrze znanych, blokowanych interfejsów API. Są w nim wyświetlane kategorie wątków w aktywnej legendzie, która znajduje się w lewym dolnym rogu widoku **wątki** . W większości przypadków można zidentyfikować główną przyczynę zdarzenia blokującego, badając stosy wywołań odpowiadające zdarzeniom przełączania kontekstu.

Jeśli nie ma dopasowania stosu wywołań, Wizualizator współbieżności używa przyczyny oczekiwania dostarczonej przez [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] . Jednak [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] Kategoria może opierać się na szczegółach implementacji i może nie odzwierciedlać intencji użytkownika. Na przykład program [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] raportuje przyczynę oczekiwania na zablokowanie natywnej, cienkiej blokady czytnika i/O zamiast synchronizacji.

Widok **wątków** zawiera również zależności między wątkami. Na przykład, jeśli określisz wątek, który jest zablokowany w obiekcie synchronizacji, można znaleźć wątek, który go odblokował. Można przeanalizować stos wywołań dla wątku odblokowywania w punkcie, gdy odblokowuje drugi.

Widoku **wątki** można użyć do:

- Zidentyfikuj przyczyny braku odpowiedzi interfejsu użytkownika w niektórych fazach wykonywania.
- Określ czas, w którym wykorzystano blokowanie synchronizacji, operacji we/wy, błędów stron i innych zdarzeń.
- Odkryj stopień zakłóceń od innych procesów, które są wykonywane w systemie.
- Identyfikuj problemy z równoważeniem obciążenia na potrzeby wykonywania równoległego.
- Znajdź przyczyny nieoptymalnej lub nieistniejącej skalowalności. Na przykład Dlaczego wydajność aplikacji równoległej nie zwiększa się, gdy są dostępne więcej rdzeni logicznych.
- Poznaj stopień współbieżności w aplikacji, aby pomóc w przetwarzanie równoległe.
- Identyfikuj zależności między wątkami procesów roboczych i ścieżkami krytycznymi wykonywania.

## <a name="use-threads-view"></a>Użyj widoku wątków

Aby rozpocząć Wizualizator współbieżności, wybierz pozycję **Analizuj**  >  **Wizualizator współbieżności**, a następnie wybierz opcję, na przykład **Uruchom nowy proces**.

Wizualizator współbieżności uruchamia aplikację i zbiera ślady do momentu wybrania opcji **Zatrzymaj zbieranie**. Wizualizator analizuje następnie ślad i wyświetla wyniki na stronie raportu śledzenia.

Wybierz kartę **wątki** w lewym górnym rogu raportu, aby otworzyć widok **wątki** .

![Widok wątków](../profiling/media/threadsviewnarrowing.png "Widok wątków")

Wybierz przedziały czasu i wątki, aby rozpocząć analizę wydajności.

## <a name="timeline-analysis"></a>Analiza osi czasu

Górną częścią widoku **wątki** jest oś czasu. Na osi czasu są wyświetlane działania wszystkich wątków w procesie oraz wszystkie urządzenia dysku fizycznego na komputerze-hoście. Wyświetla również zdarzenia dotyczące aktywności procesora GPU i znaczników.

Na osi czasu oś x to czas, a na osi y jest kilka kanałów:

- Dwa kanały we/wy dla każdego dysku w systemie, jeden kanał do odczytu i jeden dla operacji zapisu.
- Kanał dla każdego wątku w procesie.
- Kanały znacznika, jeśli istnieją zdarzenia znacznika w śladzie. Kanały znaczników początkowo pojawiają się w obszarze kanałów wątku, które wygenerowały te zdarzenia.
- Kanały procesora GPU.

Początkowo wątki są sortowane w kolejności, w której zostały utworzone, więc wątek głównej aplikacji jest pierwszy. Wybierz inną opcję z listy rozwijanej **Sortuj według** , aby posortować wątki według innego kryterium, takiego jak **wykonanie**.

Kolory osi czasu wskazują stan wątku w danym momencie. Zielone segmenty są wykonywane, a czerwone segmenty są blokowane na potrzeby synchronizacji, żółte segmenty są zastępujące, a purpurowe segmenty są włączane we/wy urządzenia.

Możesz powiększyć widok, aby wyświetlić bardziej szczegółowe informacje, lub pomniejszyć, aby wyświetlić dłuższy przedział czasu. Wybierz segmenty i punkty na grafie, aby uzyskać szczegółowe informacje na temat kategorii, czasów rozpoczęcia, opóźnień i Stanów stosu wywołań.

Użyj osi czasu, aby przeanalizować równowagę służbową między wątkami, które są uwzględnione w pętli równoległej, lub w zadaniach współbieżnych. Jeśli jeden wątek trwa dłużej niż inne, może to oznaczać, że działanie nie jest zrównoważone. Aby zwiększyć wydajność aplikacji, można równomiernie rozpowszechnić działania między wątki.

Jeśli tylko jeden wątek jest wykonywany w danym momencie, aplikacja może nie być w pełni wykorzystywać współbieżności w systemie. Możesz użyć wykresu osi czasu, aby przejrzeć zależności między wątkami, a także relacje czasowe między blokowaniem i zablokowanym wątkiem. Aby zmienić rozmieszczenie wątków, wybierz wątek, a następnie wybierz ikonę w górę lub w dół na pasku narzędzi.

Można ukryć wątki, które nie działają lub są całkowicie zablokowane, ponieważ ich statystyki są nieistotne i mogą CLOG raporty. Ukryj wątki, wybierając ich nazwy, a następnie wybierając ikony **Ukryj wybrane wątki** lub **Ukryj wszystkie z wyjątkiem wybranych wątków** na pasku narzędzi. Aby zidentyfikować wątki do ukrycia, wybierz link **podsumowania na wątek** w lewym dolnym rogu. Na wykresie **podsumowującym wątek** można ukryć wątki, które nie mają aktywności.

### <a name="thread-execution-details"></a>Szczegóły wykonania wątku
Aby uzyskać bardziej szczegółowe informacje na temat segmentu wykonywania, wybierz punkt na zielonym segmencie osi czasu. Wizualizator współbieżności wyświetla czarny znak daszki nad wybranym punktem i pokazuje jego stos wywołań na **bieżącej** karcie dolnego okienka. Można wybrać wiele punktów w segmencie wykonywania.

>[!NOTE]
>Wizualizator współbieżności może nie być w stanie rozpoznać zaznaczenia w segmencie wykonywania, jeśli czas trwania segmentu jest krótszy niż jedna milisekunda.

Aby uzyskać profil wykonywania dla wszystkich nieukrytych wątków w aktualnie wybranego zakresu czasu, wybierz opcję **wykonywanie** w legendzie w lewym dolnym rogu.

### <a name="thread-blocking-details"></a>Szczegóły blokowania wątku
Aby uzyskać informacje o określonym regionie w wątku, umieść kursor nad tym regionem na osi czasu, aby wyświetlić etykietkę narzędzia. Etykietka narzędzia zawiera informacje, takie jak kategoria, godzina rozpoczęcia i opóźnienie. Wybierz region, aby wyświetlić stos wywołań w tym momencie na **bieżącej** karcie dolnego okienka. W okienku wyświetlane są także kategorie, opóźnienie i blokowanie interfejsu API, jeśli istnieje jeden i odblokowywanie wątku, jeśli istnieje. Badając stos wywołań, można określić podstawowe przyczyny zdarzeń blokowania wątków.

Ścieżka wykonywania może mieć kilka zdarzeń blokowania. Aby sprawdzić te elementy przez zablokowanie kategorii i wyszukanie obszarów problemów szybciej, wybierz kategorię blokującą w legendzie po lewej stronie.

### <a name="dependencies-between-threads"></a>Zależności między wątkami
Wizualizator współbieżności przedstawia zależności między wątkami, dzięki czemu można określić, co zablokowany wątek próbował wykonać i jakie inne wątki obsługują do wykonania.

Aby określić, który wątek odblokował inny wątek, wybierz segment blokujący na osi czasu. Jeśli Wizualizator współbieżności może określić wątek odblokowywania, rysuje wiersz między wątkiem odblokowywania i segmentem wykonywania, który następuje po segmencie bloku. Wybierz kartę **Odblokuj stos** w dolnym okienku, aby wyświetlić odpowiedni stos wywołań.

## <a name="profile-reports"></a>Raporty profilowe
Poniżej wykresu osi czasu jest okienkiem z kartami **raport o profilach**, **Bieżąca** i **odblokowywanie stosu** . Raporty są automatycznie aktualizowane, gdy zmienisz wybór osi czasu i wątków. W przypadku dużych śladów okienko raporty może być tymczasowo niedostępne podczas obliczania aktualizacji.

### <a name="profile-report-tab"></a>Karta raport o profilu

**Raport profilu** ma dwa filtry:

- Aby odfiltrować wpisy drzewa wywołań, w przypadku których spędzano niewielki czas, wpisz wartość filtru z przedziału od 0 do 99 procent w polu **obniżka szumów** . Wartość domyślna to 2 procent.
- Aby wyświetlić drzewa wywołań tylko dla kodu, zaznacz pole wyboru **tylko mój kod** . Aby wyświetlić wszystkie drzewa wywołań, wyczyść pole wyboru.

Karta **raport o profilu** zawiera raporty dotyczące kategorii i linków w legendzie. Aby wyświetlić raport, wybierz jeden z wpisów po lewej stronie:

- **Wykonanie** Raport **wykonywania** pokazuje podział czasu, przez który aplikacja wykorzystała z wykonywania.

  Aby znaleźć wiersz kodu, w którym jest poświęcony czas wykonywania, rozwiń drzewo wywołań i w menu skrótów dla wpisu drzewa wywołań wybierz opcję **Wyświetl źródło** lub **Wyświetl Lokacje wywołań**. **Widok źródło** lokalizuje wykonany wiersz kodu. **Wyświetl Lokacje wywołań** lokalizuje wiersz kodu, który został wywołany. Jeśli istnieje tylko jeden wiersz witryny wywołania, jego kod jest wyróżniony. Jeśli istnieje kilka witryn wywołań, wybierz tę, która ma się pojawić w oknie dialogowym, a następnie wybierz pozycję **Przejdź do źródła**. Często jest to najbardziej przydatne do lokalizowania lokacji wywołań, która ma najwięcej wystąpień, w większości przypadków lub obu. Aby uzyskać więcej informacji, zobacz [raport profil wykonywania](../profiling/execution-profile-report.md).

- **Synchronizacja** Raport **synchronizacji** przedstawia wywołania, które są odpowiedzialne za bloki synchronizacji, oraz łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [godzina synchronizacji](../profiling/synchronization-time.md).

- **we/wy** Raport **we/wy** przedstawia wywołania, które są odpowiedzialne za bloki we/wy oraz łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji we/wy (Widok wątków)](../profiling/i-o-time-threads-view.md).

- **Tryb uśpienia** Raport **uśpienia** zawiera wywołania, które są odpowiedzialne za bloki uśpienia oraz łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).

- **Zarządzanie pamięcią** Raport **Zarządzanie pamięcią** zawiera wywołania, w których wystąpiły bloki zarządzania pamięcią, oraz łączny czas blokowania każdego stosu wywołań. Te informacje służą do identyfikowania obszarów, które mają nadmierne problemy z stronicowaniem lub odzyskiwaniem pamięci.  Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).

- **Zastępujący** Raport  przeniesień pokazuje, gdzie procesy w systemie zastępują bieżący proces, i poszczególne wątki, które zastąpiły wątki w bieżącym procesie. Te informacje służą do identyfikowania procesów i wątków, które są najbardziej odpowiedzialne za przeznaczenie. Aby uzyskać więcej informacji, zobacz [czas zastępujący](../profiling/preemption-time.md).

- **Przetwarzanie interfejsu użytkownika** Raport **przetwarzania interfejsu użytkownika** przedstawia wywołania, które są odpowiedzialne za bloki przetwarzania interfejsu użytkownika oraz łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).

- **Na podsumowanie wątku** Wybierz opcję **Podsumowanie poszczególnych wątków** , aby wyświetlić wykres przedstawiający stan wątków dla aktualnie wybranego interwału czasu. Kolumny kodowane kolorem przedstawiają łączny czas, w którym każdy wątek jest wykonywany, zablokowany, we/wy i inne Stany. Wątki są oznaczone etykietami u dołu. Gdy dostosowujesz poziom powiększenia na wykresie osi czasu, ten wykres zostanie automatycznie zaktualizowany.

  Na niektórych poziomach powiększenia niektóre wątki mogą nie być wyświetlane na wykresie. Gdy tak się stanie, wielokropek (**...**) pojawia się po prawej stronie. Jeśli żądany wątek nie jest wyświetlany, można ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [raport podsumowujący wątek](../profiling/per-thread-summary-report.md).

- **Operacje na dyskach** Wybierz **operacje dyskowe** , aby wyświetlić procesy i wątki związane z we/wy dysku dla bieżącego procesu, plików, które zostały naruszone (na przykład dll, które zostały załadowane), liczby odczytanych bajtów i innych informacji. Za pomocą tego raportu można oszacować czas spędzony na uzyskiwaniu dostępu do plików podczas wykonywania, zwłaszcza gdy proces wydaje się być powiązany we/wy. Aby uzyskać więcej informacji, zobacz [raport operacji dyskowych](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Bieżąca karta
Na tej karcie jest wyświetlany stos wywołań dla wybranego punktu w segmencie wątku na wykresie osi czasu. Stosy wywołań są przycinane, aby pokazać tylko działanie, które jest powiązane z Twoją aplikacją.

### <a name="unblocking-stack-tab"></a>Odblokowywanie karty stosu
Na tej karcie jest wyświetlany wątek odblokowywania wybranego wątku oraz odblokowywanie stosu wywołań.

## <a name="see-also"></a>Zobacz także
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
