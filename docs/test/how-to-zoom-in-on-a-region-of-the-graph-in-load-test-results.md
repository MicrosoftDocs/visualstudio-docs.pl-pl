---
title: Powiększ Wykresy wyników testu obciążenia
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 836e4f30e2c84bf0093366f4cc38a2cb7f58b545
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287028"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Instrukcje: powiększanie obszaru wykresu w wynikach testu obciążenia

Po zakończeniu testu obciążenia można użyć pasków powiększenia, aby powiększyć i przewinąć do regionu grafu. Powiększając, można sprawdzić dane, które zostały wygenerowane podczas przebiegu testu obciążenia, bardziej szczegółowo.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Powiększenie jest dostępne tylko wtedy, gdy analizujesz wynik zakończonego testu obciążenia, a nie w czasie obserwacji wyników testu.

Kontrolka powiększenia jest widoczna tylko w **analizatorze testu obciążenia** , gdy oglądasz wynik testu obciążenia w trybie powiększania. Tryb powiększania jest ustalany w widoku wykresu, gdy zakończono test obciążenia lub załadowano test obciążenia, który został wcześniej uruchomiony. Kontrolki powiększenia można pokazać lub ukryć na wykresach, używając **kontrolek Pokaż powiększenie** na pasku narzędzi.

**Poziom powiększenia osi x** można dostosować w celu przeanalizowania określonych okresów czasu podczas testu obciążenia. **Pionowe powiększenie osi y** można dostosować w celu analizowania określonych zakresów wartości dla liczników, które są uwzględnione w grafie.

Zarówno **poziomy oś czasu** , jak i kontrolka powiększenia **zakresu wartości pionowej** można dostosować za pomocą myszy. **Formant oś czasu w poziomie** można również dostosować przy użyciu klawiszy strzałek w lewo i w prawo. Używając klawiszy strzałek, aby dostosować kontrolkę powiększenia, można w danym momencie dostosować interwał próbkowania do zakresu systemu Windows. Użycie klawiszy **SHIFT** i Strzałka powoduje korektę 10 interwałów próbkowania.

Aby dostosować kontrolkę powiększenia przy użyciu klawisza Strzałka, najpierw ustaw fokus na kontrolce powiększenia przy użyciu klawisza **Tab** . Gdy lewy suwak ma fokus, klawisze strzałek przenoszą początkową granicę okna powiększenia o 1 interwał w lewo lub w prawo. Gdy fokus jest na suwaku Centralnym, możesz użyć klawiszy strzałek, aby przewinąć okno powiększenia w lewo lub w prawo 1 interwał próbkowania bez zmiany rozmiaru okna powiększenia. A wreszcie suwak po prawej stronie przesuwa, rozszerza lub zmniejsza zakres końca okna powiększenia o 1 interwał próbkowania.

Aby przywrócić kontrolki w poziomie i w pionie, aby pokazać pełną oś czasu i zakres wartości, można użyć opcji **Powiększ pozioma** , opcji **Powiększ w pionie** lub **pomniejszej** opcji w menu podręcznym wykresu.

> [!TIP]
> Aby włączyć lub wyłączyć automatyczną synchronizację powiększenia w poziomie, można użyć **kontrolek Powiększ poziomy** na pasku narzędzi. W przypadku synchronizacji w systemie wszystkie powiększające się dane są również stosowane do innych wykresów w widoku wykresy.

![Kontrolka powiększenia widoku wykresu](../test/media/ltest_zoomcontrol.png)

Na poprzedniej ilustracji, system na wykresie **testowym** został powiększony, aby zbadać problemy z progami. Naruszenia progowe zostały włączone przy użyciu opcji **Pokaż naruszenia progu na grafie** z listy rozwijanej **Opcje wykresu** na pasku narzędzi.

Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Wykresy wyświetlania

Przed zmianą wyświetlania wykresu przez Powiększanie lub zmniejszenie lub przewinięcie, wykonaj poniższą procedurę, aby wyświetlić wykresy.

Aby wyświetlić wykresy:

1. Uruchom test obciążeniowy, aż zostanie zakończony.

2. Na końcu przebiegu testu obciążenia wybierz pozycję **tak** w oknie dialogowym z pytaniem o Wyświetlanie wyników z magazynu wyników testów obciążenia.

     \- oraz

     Wyświetl szczegóły wcześniej uruchomionego testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [jak: uzyskiwanie dostępu do wyników testów obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md).

3. Wybierz **wykresy** , jeśli wykresy nie są wyświetlane.

4. Jeśli paski powiększenia nie są wyświetlane, wybierz **Pokaż kontrolki powiększenia**.

     Dla każdego grafu dostępne są dwa paski powiększenia. Pasek powiększenia, który kontroluje skalę pionową, pojawia się na lewo od wykresu. Na wykresie zostanie wyświetlony pasek powiększenia kontrolujący skalowanie w poziomie.

     Każdy pasek powiększenia ma dwa uchwyty. Uchwyt jest prostokątnym obszarem na każdym końcu paska powiększenia.

## <a name="zoom-and-scroll"></a>Powiększanie i przewijanie

Gdy jest wyświetlanych wiele wykresów, można je synchronizować tak, aby wyświetlały tę samą część przebiegu testu obciążenia.

### <a name="to-synchronize-zooming-and-scrolling"></a>Aby synchronizować powiększanie i przewijanie

1. W **analizatorze testu obciążenia**wybierz kolejno opcje **Synchronizuj poziomy powiększenia**.

     Po wybraniu przycisku **Synchronizuj kontrolki powiększenia poziomego** , powiększanie i przewijanie skali czasu dla pojedynczego wykresu powoduje również powiększenie i przewinięcie skali czasu dla innych wykresów.

2. Ponownie wybierz pozycję **Synchronizuj kontrolki powiększenia poziomego**.

     Gdy nie wybrano przycisku **Synchronizuj kontrolki powiększenia poziomego** , powiększanie i przewijanie skali czasu poszczególnych wykresów wpływa tylko na ten wykres.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Aby powiększyć i przewinąć do regionu wykresu

1. Na pasku powiększenia pod wykresem przeciągnij uchwyt po lewej stronie w prawo.

     Ta wartość powiększa się w tej ostatniej części przebiegu testu. Podobnie, przeciągając uchwyt po prawej stronie do lewego powiększenia w przypadku wcześniejszych części przebiegu testu.

2. Aby powiększyć w określonym obszarze, przesuwanie obydwu uchwytów do środka grafu.

     Im bliżej dwa uchwyty, tym większa jest powiększanie, aby wyświetlić krótsze i bardziej precyzyjne segmenty testu obciążenia.

     Wybierz środkową sekcję na pasku powiększenia, a następnie przeciągnij ją w celu przewinięcia do określonego punktu w teście obciążenia.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Aby powiększyć do regionu grafu, wybierając i przeciągając

1. Wybierz wykres na jednym końcu obszaru powiększenia.

2. Przeciągnij wskaźnik myszy na drugi koniec obszaru powiększenia.

3. Zwolnij przycisk myszy.

    Spowoduje to powiększenie obszaru zdefiniowanego przez wybranie i przeciągnięcie.

   Poniższa procedura zawiera opis sposobu szybkiego powiększania bez konieczności dostosowywania zakończenia paska powiększenia.

### <a name="to-zoom-out"></a>Aby pomniejszyć

1. Kliknij prawym przyciskiem myszy wykres powiększony o większy rozmiar.

2. W menu skrótów wybierz pozycję **Powiększ w poziomie**.

     Powoduje to pomniejszenie, aby pokazać cały czas trwania przebiegu testu obciążenia.

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
