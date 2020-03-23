---
title: Powiększanie wykresów wyników testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a22f1a9b6aa772224b217b5de4136687df1462a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594373"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Jak: Powiększenie regionu wykresu w wynikach testu obciążenia

Po zakończeniu testu obciążenia można użyć pasków powiększenia, aby powiększyć i przewinąć do regionu wykresu. Powiększając, można sprawdzić dane, które zostały wygenerowane podczas testu obciążenia uruchomić w dokładniejszych szczegółach.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Powiększenie jest dostępne tylko podczas analizowania wyniku testu obciążenia zakończonego, a nie podczas obserwowania wyników uruchomionego testu.

Formant powiększenia jest widoczny tylko w **analizatorze testu obciążenia** podczas wyświetlania wyniku testu obciążenia w trybie powiększania. Tryb powiększania jest ustanawiany w widoku Graf po zakończeniu testu obciążenia lub załadowaniu testu obciążenia, który został wcześniej uruchomiony. Kontrolki powiększenia na wykresach można wyświetlać lub ukrywać, używając **przycisków Pokaż kontrolki powiększenia** na pasku narzędzi.

**Poziome powiększenie osi x** można dostosować do analizy określonych okresów podczas testu obciążenia. **Powiększenie osi y** można dostosować do analizowania określonych zakresów wartości dla liczników, które są zawarte na wykresie.

Za pomocą myszy można dostosować zarówno **poziomą oś czasu,** jak i elementy sterujące powiększeniem **zakresu wartości pionowej.** Formant **osi czasu w poziomie** można również regulować za pomocą klawiszy strzałek w lewo i w prawo. Za pomocą klawiszy strzałek, aby dostosować formant powiększenia, można dostosować zakres okien przez 1 interwał próbkowania naraz. Za pomocą **klawiszy Shift** i klawiszy strzałek wprowadza regulację 10 interwałów próbkowania.

Aby dostosować kontrolkę powiększenia za pomocą klawisza strzałek, najpierw ustaw fokus na formancie powiększenia za pomocą **klawisza Tab.** Gdy lewy suwak ma fokus, klawisze strzałek przesuną początkową granicę okna powiększenia o 1 interwał w lewo lub w prawo. Gdy fokus znajduje się na środkowym suwaku, można użyć klawiszy strzałek, aby przewinąć okno powiększenia w lewo lub w prawo 1 interwał próbkowania bez zmiany rozmiaru okna powiększenia. I wreszcie, prawy suwak strony przesuwa, rozszerzając lub zmniejszając zakres końca okna powiększenia o 1 interwał próbkowania.

Aby przywrócić kontrolki powiększenia poziomego i pionowego w celu wyświetlenia pełnej osi czasu i zakresów wartości, można użyć opcji **Pomniejsz poziome,** opcji **Pomniejsz w pionie** lub **Opcji Pomniejsz oba** w wyskakującym menu na wykresie.

> [!TIP]
> Za pomocą **opcji Synchronizuj elementy sterujące powiększenia poziomego** na pasku narzędzi można włączyć lub wyłączyć automatyczną synchronizację powiększenia poziomego. Po wliczeniu synchronizacji każde powiększanie zastosowane do wykresu zostanie również zastosowane do innych wykresów w widoku Wykresy.

![Sterowanie powiększeniem widoku wykresu](../test/media/ltest_zoomcontrol.png)

Na poprzedniej ilustracji system w obszarze wykres **testowy** został powiększony w celu zbadania problemów progowych. Naruszenia progu zostały włączone przy użyciu **Pokaż naruszenia progu na wykresie** z listy rozwijanej Opcje **wykresu** na pasku narzędzi.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Wyświetlanie wykresów

Przed zmianą wyświetlania wykresu przez powiększanie, pomniejszanie lub przewijanie, wykonaj tę procedurę, aby wyświetlić wykresy.

Aby wyświetlić wykresy:

1. Uruchom test obciążeniowy, aż zostanie zakończony.

2. Na końcu przebiegu testu obciążenia wybierz przycisk **Tak** w oknie dialogowym z pytaniem o wyświetlanie wyników z magazynu wyników testu obciążenia.

     \-lub -

     Wyświetl szczegóły wcześniej uruchomionego testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

3. **Wybierz wykresy,** jeśli wykresy nie są wyświetlane.

4. Jeśli paski powiększenia nie są wyświetlane, wybierz pozycję **Pokaż kontrolki powiększenia**.

     Dla każdego wykresu dostępne są dwa paski powiększenia. Pasek powiększenia sterujący skalą pionową pojawia się po lewej stronie wykresu. Pasek powiększenia sterujący skalą poziomą pojawia się pod wykresem.

     Każdy pasek powiększenia ma dwa uchwyty. Uchwyt jest prostokątnym obszarem na każdym końcu paska powiększenia.

## <a name="zoom-and-scroll"></a>Powiększanie i przewijanie

Jeśli masz wiele wykresów wyświetlanych, można zachować je zsynchronizowane tak, aby wyświetlić tę samą część przebiegu testu obciążenia.

### <a name="to-synchronize-zooming-and-scrolling"></a>Aby zsynchronizować powiększanie i przewijanie

1. W **analizatorze testu obciążenia**wybierz pozycję **Synchronizuj elementy sterujące powiększenia poziomego**.

     Po wybraniu przycisku **Synchronizuj elementy sterujące powiększeniem w poziomie** powiększanie i przewijanie skali czasu poszczególnych wykresów powoduje również powiększanie i przewijanie skali czasu innych wykresów.

2. Ponownie wybierz pozycję **Synchronizuj elementy sterujące powiększenia poziomego**.

     Gdy przycisk **Synchronizuj elementy sterujące powiększenia poziomego** nie jest zaznaczony, powiększanie i przewijanie skali czasu poszczególnych wykresów ma wpływ tylko na ten wykres.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Aby powiększyć i przewinąć do regionu wykresu

1. Na pasku powiększenia pod wykresem przeciągnij lewy uchwyt w prawo.

     Spowoduje to powiększenie w drugiej części przebiegu testowego. Podobnie przeciąganie uchwytu po prawej stronie w lewo powoduje powiększenie wcześniejszych części przebiegu testowego.

2. Aby powiększyć określony obszar, przesuń oba uchwyty w kierunku środka wykresu.

     Im bliżej dwóch uchwytów są do siebie, tym bardziej powiększasz, aby wyświetlić krótsze, drobniejsze segmenty testu obciążenia.

     Wybierz środkową część paska powiększenia, a następnie przeciągnij ją, aby przewinąć do określonego punktu w teście obciążenia.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Aby powiększyć obszar wykresu, wybierając i przeciągając

1. Wybierz wykres na jednym końcu obszaru powiększenia.

2. Przeciągnij wskaźnik myszy na drugi koniec obszaru powiększenia.

3. Zwolnij przycisk myszy.

    Spowoduje to powiększenie zdefiniowanego obszaru przez wybranie i przeciągnięcie.

   W poniższej procedurze opisano sposób szybkiego pomniejszania bez konieczności regulacji końców paska powiększenia.

### <a name="to-zoom-out"></a>Aby pomniejszyć

1. Kliknij prawym przyciskiem myszy powiększony wykres.

2. W menu skrótów wybierz polecenie **Pomniejsz poziomo**.

     Spowoduje to pomniejszenie, aby wyświetlić cały czas trwania przebiegu testu obciążenia.

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
