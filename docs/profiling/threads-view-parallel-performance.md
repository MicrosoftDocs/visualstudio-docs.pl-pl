---
title: Widok wątków w wizualizatorze współbieżności | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 4382a21a68848a758f3d4cd37a8528722927691c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62973760"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Widok wątków w wizualizatorze współbieżności

**Widok wątków** jest najbardziej szczegółowy i bogaty w funkcje widoku w wizualizatora współbieżności. W widoku **Wątki** można zidentyfikować, które wątki wykonują kod podczas segmentu wykonywania i analizować, czy wątki są wykonywane lub blokowane z powodu synchronizacji, we/wy lub z innych powodów. **Wątki** wyświetlają raporty również profil wykonania drzewa stosu wywołań i odblokowanie wątków.

Podczas wykonywania wątków wizualizator współbieżności zbiera przykłady. Gdy wątek przestał wykonywać, wizualizator sprawdza wszystkie zdarzenia kontekstu systemu operacyjnego dla wątku. Przełączniki kontekstu mogą wystąpić, ponieważ:

- Wątek jest zablokowany na prymityw synchronizacji.
- Kwant wątku wygasa.
- Wątek powoduje zablokowanie żądania we/wy.

Wizualizator współbieżności kategoryzuje zdarzenia wątek i przełącznik kontekstu i przeszukuje stosy wywołań wątków w poszukiwaniu dobrze znanych blokowych interfejsów API. Wyświetla kategorie wątków w aktywnej legendzie w lewym dolnym po lewej stronie w widoku **Wątki.** W większości przypadków można zidentyfikować główną przyczynę zdarzenia blokowania, badając stosy wywołań, które odpowiadają zdarzeń przełączania kontekstu.

Jeśli nie ma dopasowania stosu wywołań, wizualizator współbieżności używa przyczyny oczekiwania dostarczonej przez [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Jednak [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategoria może być oparta na szczegółach implementacji i może nie odzwierciedlać intencji użytkownika. Na przykład [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] zgłasza przyczynę oczekiwania do blokowania na natywnej blokady czytnika slim jako we/wy zamiast synchronizacji.

**Widok wątków** pokazuje również zależności między wątkami. Na przykład jeśli zidentyfikować wątek, który jest zablokowany na obiekcie synchronizacji, można znaleźć wątek, który odblokował go. Można sprawdzić stos wywołań dla wątku odblokowywania w punkcie, gdy odblokowany drugi.

Widoku **Wątki** można użyć do:

- Identyfikowanie przyczyn interfejsu użytkownika (UI) aplikacji nie odpowiada podczas niektórych faz wykonywania.
- Określ czas spędzony na blokowaniu synchronizacji, we/wy, błędach strony i innych zdarzeniach.
- Odkryj stopień zakłóceń z innych procesów wykonywanych w systemie.
- Identyfikowanie problemów równoważenia obciążenia do wykonywania równoległego.
- Znajdź przyczyny nieoptymalnej lub nieistniejącej skalowalności. Na przykład dlaczego wydajność aplikacji równoległej nie poprawić, gdy więcej rdzeni logicznych są dostępne.
- Zrozumieć stopień współbieżności w aplikacji, aby pomóc w równoległości.
- Identyfikowanie zależności między wątkami roboczymi i krytycznymi ścieżkami wykonywania.

## <a name="use-threads-view"></a>Użyj widoku Wątki

Aby uruchomić wizualizator współbieżności, wybierz **pozycję Analizuj** > **wizualizator współbieżności,** a następnie wybierz opcję, taką jak **Uruchom nowy proces**.

Wizualizator współbieżności uruchamia aplikację i zbiera ślad, dopóki nie wybierzesz **Zatrzymaj kolekcji**. Wizualizator następnie analizuje śledzenia i wyświetla wyniki na stronie raportu śledzenia.

Wybierz **wątki** kartę w lewym górnym rogu w raporcie, aby otworzyć widok **Wątki.**

![Widok wątków](../profiling/media/threadsviewnarrowing.png "Widok wątków")

Wybierz przedziały czasu i wątki, aby rozpocząć analizę wydajności.

## <a name="timeline-analysis"></a>Analiza osi czasu

Górna część widoku **Wątki** jest osią czasu. Oś czasu pokazuje aktywność wszystkich wątków w procesie i wszystkich fizycznych urządzeń dyskowych na komputerze-hoście. Wyświetla również aktywność gpu i zdarzenia znacznika.

Na osi czasu oś x to czas, a na osi y kilka kanałów:

- Dwa kanały we/wy dla każdego dysku w systemie, jeden kanał do odczytów i jeden dla zapisów.
- Kanał dla każdego wątku w procesie.
- Kanały znaczników, jeśli w śledzenia występują zdarzenia znacznika. Kanały znaczników początkowo pojawiają się pod kanałami wątku, które wygenerowały te zdarzenia.
- kanałów GPU.

Początkowo wątki są sortowane w kolejności, w jakiej są tworzone, więc główny wątek aplikacji jest pierwszy. Wybierz inną opcję z listy rozwijanej **Sortuj według,** aby sortować wątki według innego kryterium, takiego jak **Wykonanie**.

Kolory osi czasu wskazują stan wątku w danym czasie. Segmenty zielone są wykonywane, czerwone segmenty są blokowane do synchronizacji, żółte segmenty są wywłaszczone, a fioletowe segmenty są zaangażowane w we/wy urządzenia.

Można powiększyć, aby wyświetlić więcej szczegółów, lub pomniejszyć, aby wyświetlić dłuższy przedział czasu. Wybierz segmenty i punkty na wykresie, aby uzyskać szczegółowe informacje o kategoriach, godzinach rozpoczęcia, opóźnieniach i stanach stosu połączeń.

Użyj osi czasu, aby zbadać równowagę pracy między wątkami, które są zaangażowane w pętli równoległej lub w równoczesnych zadań. Jeśli jeden wątek trwa dłużej niż inne, praca może być niezrównoważona. Możesz poprawić wydajność aplikacji, rozdzielając pracę bardziej równomiernie między wątki.

Jeśli tylko jeden wątek jest wykonywany w momencie, aplikacja może nie być przy pełnym wykorzystaniu współbieżności w systemie. Wykres osi czasu służy do badania zależności między wątkami i relacji czasowych między blokowanie i zablokowane wątki. Aby zmienić kolejność wątków, zaznacz wątek, a następnie wybierz ikonę w górę lub w dół na pasku narzędzi.

Można ukryć wątki, które nie wykonują pracy lub są całkowicie zablokowane, ponieważ ich statystyki są nieistotne i mogą zatkać raporty. Ukryj wątki, zaznaczając ich nazwy, a następnie wybierając **pozycję Ukryj zaznaczone wątki** lub **Ukryj wszystkie z wyjątkiem wybranych wątków** na pasku narzędzi. Aby zidentyfikować wątki do ukrycia, wybierz **łącze Podsumowanie na wątek** w lewym dolnym dolnym czasie. Można ukryć wątki, które nie mają działania na **wykresie podsumowanie wątku.**

### <a name="thread-execution-details"></a>Szczegóły wykonania wątku
Aby uzyskać bardziej szczegółowe informacje o segmencie wykonania, wybierz punkt na zielonym segmencie osi czasu. Wizualizator współbieżności wyświetla czarną szulację nad wybranym punktem i pokazuje jego stos wywołań na karcie **Bieżący** w dolnym okienku. Można wybrać wiele punktów w segmencie wykonania.

>[!NOTE]
>Wizualizator współbieżności może nie być w stanie rozwiązać wyboru w segmencie wykonywania, jeśli czas trwania segmentu jest krótszy niż jeden milisekunda.

Aby uzyskać profil wykonania dla wszystkich wątków nieukrytych w aktualnie wybranym zakresie czasu, wybierz **wykonanie** w legendzie w lewym dolnym dolnym po lewej stronie.

### <a name="thread-blocking-details"></a>Szczegóły blokowania wątków
Aby uzyskać informacje o określonym regionie w wątku, umieść wskaźnik myszy na tym regionie na osi czasu, aby wyświetlić etykietkę narzędzia. Etykietka narzędzia ma informacje, takie jak kategoria, czas rozpoczęcia i opóźnienie. Wybierz region, aby wyświetlić stos wywołań w tym momencie w bieżącym **kartę** w dolnym okienku. Okienko pokazuje również kategorię, opóźnienie, blokowanie interfejsu API, jeśli istnieje, i odblokowanie wątku, jeśli istnieje. Badając stos wywołań, można określić przyczyny zdarzeń blokowania wątków.

Ścieżka wykonywania może mieć kilka zdarzeń blokowania. Aby je sprawdzić, blokując kategorię i szybciej znaleźć obszary problemowe, wybierz kategorię blokowania w legendzie po lewej stronie.

### <a name="dependencies-between-threads"></a>Zależności między wątkami
Wizualizator współbieżności pokazuje zależności między wątkami, dzięki czemu można określić, co zablokowany wątek próbował zrobić i co inny wątek włączył go do wykonania.

Aby określić, który wątek odblokował inny wątek, wybierz segment blokujący na osi czasu. Jeśli wizualizator współbieżności można określić odblokowywanie wątku, rysuje linię między wątku odblokowywania i segmentu wykonującego, który następuje segment blokowania. Wybierz kartę **Odblokowywanie stosu** w dolnym okienku, aby wyświetlić odpowiedni stos wywołań.

## <a name="profile-reports"></a>Raporty profilowe
Poniżej wykresu osi czasu znajduje się okienko z **kartami Raportu profilu**, **Bieżący**i **Odblokowywanie** raportu stosu. Raporty są automatycznie aktualizowane w miarę zmiany zaznaczeń osi czasu i wątków. W przypadku dużych śladów okienko raportów może być tymczasowo niedostępne podczas obliczania aktualizacji.

### <a name="profile-report-tab"></a>Karta Raport profilu

**Raport profilu** zawiera dwa filtry:

- Aby odfiltrować wpisy drzewa wywołań, w których spędzono niewiele czasu, wpisz wartość filtru z zakresu od 0 do 99 procent w polu **Redukcja szumów w** polu. Wartość domyślna to 2 procent.
- Aby wyświetlić drzewa połączeń tylko dla kodu, zaznacz pole wyboru **Tylko mój kod.** Aby wyświetlić wszystkie drzewa połączeń, wyczyść to pole wyboru.

Na karcie **Raport profilu** są wyświetlane raporty dotyczące kategorii i łączy w legendzie. Aby wyświetlić raport, wybierz jeden z wpisów po lewej stronie:

- **Wykonanie** Raport **wykonanie** pokazuje podział czasu aplikacji spędzonego w wykonaniu.

  Aby znaleźć wiersz kodu, w którym spędzany jest czas wykonywania, rozwiń drzewo wywołań i w menu skrótów dla wpisu drzewa wywołań, wybierz **pozycję Wyświetl źródło** lub Wyświetl **witryny połączeń**. **Wyświetl źródło** lokalizuje wykonany wiersz kodu. **Wyświetl witryny wywołań** lokalizuje wiersz kodu, który nazywa się wykonywany wiersz. Jeśli istnieje tylko jeden wiersz lokacji wywołania, jego kod jest wyróżniony. Jeśli istnieje kilka witryn wywołań, wybierz odpowiednią witrynę w oknie dialogowym, a następnie wybierz pozycję **Przejdź do źródła**. Często najbardziej przydatne jest zlokalizowanie witryny wywołania, która ma najwięcej wystąpień, najwięcej czasu lub oba te elementy. Aby uzyskać więcej informacji, zobacz [Raport profilu wykonania](../profiling/execution-profile-report.md).

- **Synchronizacja** Raport **synchronizacji** pokazuje wywołania, które są odpowiedzialne za bloki synchronizacji, wraz z całkowitym czasem blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas synchronizacji](../profiling/synchronization-time.md).

- **We/Wy** Raport **We/Wy** pokazuje wywołania, które są odpowiedzialne za bloki we/wy, wraz z całkowitym czasem blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas we/wy (widok wątków)](../profiling/i-o-time-threads-view.md).

- **Sen** Raport **Uśpienie** pokazuje wywołania, które są odpowiedzialne za bloki uśpienia, wraz z całkowitym czasem blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas uśpienia](../profiling/sleep-time.md).

- **Zarządzanie pamięcią** Raport **Zarządzanie pamięcią** pokazuje wywołania, w których wystąpiły bloki zarządzania pamięcią, wraz z całkowitym czasem blokowania każdego stosu wywołań. Te informacje można wykorzystać do identyfikowania obszarów, które mają nadmierne problemy z stronicowania lub wyrzucania elementów bezużytecznych.  Aby uzyskać więcej informacji, zobacz [Czas zarządzania pamięcią](../profiling/memory-management-time.md).

- **Wywłaszczenie** Raport **wywłaszczenia** pokazuje, gdzie procesy w systemie wywłaszczył bieżący proces i poszczególnych wątków, które zastąpiły wątki w bieżącym procesie. Te informacje można użyć do identyfikowania procesów i wątków, które są najbardziej odpowiedzialne za wywłaszczenie. Aby uzyskać więcej informacji, zobacz [Czas wywłaszczenia](../profiling/preemption-time.md).

- **Przetwarzanie interfejsu użytkownika** Raport **przetwarzania interfejsu** użytkownika pokazuje wywołania, które są odpowiedzialne za bloki przetwarzania interfejsu użytkownika, wraz z całkowitym czasem blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).

- **Podsumowanie na wątek** Wybierz **opcję Podsumowanie na wątek,** aby wyświetlić wykres przedstawiający stan wątków dla aktualnie wybranego przedziału czasu. Kolumny oznaczone kolorami pokazują całkowity czas spędzony w ciągu każdego wątku w przebiegu, zablokowany, we/wy i inne stany. Gwinty są oznaczone na dole. Po dostosowaniu poziomu powiększenia na wykresie osi czasu ten wykres jest automatycznie aktualizowany.

  W niektórych poziomach powiększenia niektóre wątki mogą nie być wyświetlane na wykresie. W takim przypadku po prawej stronie pojawią się elipsy (**...**). Jeśli żądany wątek nie jest wyświetlany, można ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [Raport podsumowujący dla wątków](../profiling/per-thread-summary-report.md).

- **Operacje na dysku** Wybierz **operacje dysków,** aby wyświetlić procesy i wątki zaangażowane w operacje/wy dysku dla bieżącego procesu, pliki, których dotknął (na przykład biblioteki DLL, które załadowali), liczbę odczytanych bajtów i inne informacje. Ten raport służy do oceny czasu spędzonego na uzyskiwaniu dostępu do plików podczas wykonywania, zwłaszcza gdy proces wydaje się być związany we/wy. Aby uzyskać więcej informacji, zobacz [Raport operacji dysku](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Bieżąca karta
Ta karta pokazuje stos wywołań dla wybranego punktu w segmencie wątku na wykresie osi czasu. Stosy wywołań są przycinane, aby wyświetlić tylko działanie, które jest związane z aplikacją.

### <a name="unblocking-stack-tab"></a>Karta Odblokowywanie stosu
Ta karta pokazuje, który wątek odblokował wybrany wątek, a stos wywołania odblokowujący.

## <a name="see-also"></a>Zobacz też
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
