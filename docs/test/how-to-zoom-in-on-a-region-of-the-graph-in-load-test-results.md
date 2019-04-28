---
title: Powiększanie wykresy wyników testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f570e2085bf9d0707bb5a8bfe33576466a6d7b41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821210"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Instrukcje: Powiększanie obszaru wykresu w wynikach testów obciążenia

Po zakończeniu testu obciążeniowego umożliwia powiększenie paski powiększyć obraz i przewiń do obszaru wykresu. Przez powiększyć, można sprawdzić dane, który został wygenerowany podczas testu obciążenia uruchamiane w bardziej szczegółowo.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Powiększ jest dostępna tylko podczas analizowania wynik zakończonego testu obciążenia, gdy występują wyniki testu.

Kontrolka powiększenia jest widoczna tylko w **analizatora testu obciążenia** podczas wyświetlania wyniku testu obciążeniowego w trybie powiększanie. Po zakończeniu testu obciążeniowego lub testu obciążenia, który został wcześniej uruchomiony jest ładowany, w widoku wykresu ustanawiany jest tryb powiększanie. Możesz pokazać lub ukryć kontrolki powiększania na wykresach przy użyciu **Pokaż formanty powiększenia** na pasku narzędzi.

**Powiększenie osi poziomej** można dopasować do analizowania danych okresach czasu podczas testu obciążeniowego. **Powiększenie osi pionowej y** można dopasować do analizowania określonej wartości zakresów liczniki, które znajdują się na wykresie.

Zarówno **osi poziomej** i **zakres wartości pionowy** kontrolki powiększania można dostosować za pomocą myszy. **Kontroli osi poziomej** również można dostosować za pomocą klawiszy Strzałka w lewo i w prawo. Za pomocą klawiszy strzałek, aby dopasować Kontrolka powiększenia, można dostosować zakresu systemu windows, interwał próbkowania 1 w danym momencie. Za pomocą **Shift** i klawiszy strzałek sprawia, że dostosowania 10 próbkowania.

Aby dostosować Kontrolka powiększenia za pomocą strzałki, najpierw ustawić fokus na Kontrolka powiększenia przy użyciu **kartę** klucza. Po aktywowaniu lewy suwak, klawiszy strzałek zostanie przesunięty początkowy granic okna powiększenia przez 1 interwału w lewej lub prawej. Gdy fokus jest ustawiony na suwaku center, można użyć klawiszy strzałek, przewiń powiększenia okna lewego lub prawego 1 interwał próbkowania bez zmiany rozmiaru okna powiększenia. A na koniec suwaka po prawej stronie zostanie przeniesiony, rozszerzenia lub ograniczenia zakresu koniec okna powiększenia przez 1 interwału próbkowania.

Aby przywrócić kontrolki powiększania poziome i pionowe, aby wyświetlić pełną oś czasu i zakresami wartości, można użyć **powiększania się poziomy** opcji **powiększenia Out pionowych** opcji lub **Pomniejsz Zarówno** opcji w menu podręcznym na wykresie.

> [!TIP]
> Możesz użyć **zsynchronizować poziomy powiększenia formantów** w pasku narzędzi, aby włączać i wyłączać synchronizację automatycznego powiększania w poziomie. W przypadku synchronizacji na wszelkie powiększania, które można zastosować do wykresu również będą stosowane do żadnych innych wykresów w widoku wykresu.

![Kontrolka powiększenia widoku wykresu](../test/media/ltest_zoomcontrol.png)

Na poprzedniej ilustracji **badanego** wykres ma powiększona, aby zbadać problemy z wartości progowej. Naruszenia progu zostały włączone za pomocą **Pokaż naruszenia progu na wykresie** z **Opcje wykresu** listy rozwijanej na pasku narzędzi.

Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Wyświetlanie wykresów

Zanim zmienisz wyświetlania wykresu powiększanie lub pomniejszanie lub przewijając, wykonaj tę procedurę, aby wyświetlić wykresy.

Aby wyświetlić wykresy:

1. Uruchom test obciążeniowy, aż zostanie zakończony.

2. Na końcu przebiegu testu obciążeniowego wybierz **tak** w oknie dialogowym z pytaniem o wyświetlaniu wyników z wyników testów obciążenia są przechowywane.

     \- lub —

     Wyświetl szczegóły wcześniej uruchomionego testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

3. Wybierz **wykresów** Jeśli wykresów nie są wyświetlane.

4. Jeśli paski powiększenia nie są wyświetlane, wybierz opcję **Pokaż formanty powiększenia**.

     Dwa paski powiększenia są dostępne dla każdego wykresu. Pasek powiększenia, który kontroluje skalowania w pionie pojawia się po lewej stronie wykresu. W obszarze wykresu zostanie wyświetlony pasek powiększenia, który kontroluje skalowanie w poziomie.

     Każdy pasek powiększenia ma dwa uchwyty. Dojście jest prostokątny obszar, na każdym końcu pasek powiększenia.

## <a name="zoom-and-scroll"></a>Powiększanie i przewijanie

W przypadku wielu wykresy wyświetlane zapewnić ich synchronizację, tak że wyświetlają one w tej samej części przebiegu testu obciążeniowego.

### <a name="to-synchronize-zooming-and-scrolling"></a>Aby zsynchronizować powiększania i przewijania

1. Na **analizatora testu obciążenia**, wybierz **zsynchronizować poziomy powiększenia kontrolki**.

     Gdy **zsynchronizować poziomy powiększenia formantów** przycisk jest zaznaczony, powiększania i przewijania Skala czasu poszczególnych wykresów również powiększa Przewija skali czasu inne wykresy.

2. Ponownie wybierz pozycję **zsynchronizować poziomy powiększenia kontrolki**.

     Gdy **zsynchronizować poziomy powiększenia formantów** przycisk nie jest zaznaczone, powiększanie i przewijanie Skala czasu poszczególnych wykresów dotyczy tylko tego wykresu.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Na powiększanie i przewijanie do obszaru wykresu

1. Na pasku powiększenia wykresu przeciągnij uchwyt po lewej stronie, aby po prawej stronie.

     To powiększa w dalszej części przebiegu testu. Podobnie przeciągając uchwyt po prawej stronie po lewej stronie powiększa wcześniejszej części przebiegu testu.

2. Aby powiększyć konkretnego obszaru, przesuń zarówno uchwyty do środka wykresu.

     Im bliżej obsługuje dwa są ze sobą, tym bardziej powiększania Aby wyświetlić segmenty krótszych, bardziej precyzyjną testu obciążeniowego.

     Wybierz Centrum części pasek powiększenia, a następnie przeciągnij go do przewijania do określonego punktu w teście obciążeniowym.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Aby powiększyć do obszaru wykresu, wybierając i przeciągając

1. Wybierz wykres na jednym końcu obszaru powiększenia.

2. Przeciągnij kursor na końcu w obszarze powiększenia.

3. Zwolnij przycisk myszy.

    To zwiększa obszar zdefiniowany przez wybranie i przeciągając.

   Poniższa procedura opisuje sposób szybko pomniejszyć bez konieczności dostosować zakończenia pasek powiększenia.

### <a name="to-zoom-out"></a>Aby pomniejszyć

1. Kliknij prawym przyciskiem myszy wykres powiększonej.

2. W menu skrótów wybierz **powiększania się poziomy**.

     To powiększa się, aby wyświetlić cały czas trwania testu obciążenia Uruchom.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)