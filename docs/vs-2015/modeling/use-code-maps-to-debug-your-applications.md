---
title: Używanie map kodu do debugowania aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 33f8d583c369ae365b8d7063a7b0c1d6353a3c56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659479"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapy kodu mogą pomóc uniknąć utraty w dużych bazach kodu, nieznanego kodu lub starszego kodu. Na przykład podczas debugowania możesz chcieć spojrzeć na kod w wielu plikach i projektach. Za pomocą map kodu można nawigować po fragmentach kodu i zrozumieć relacje między nimi. Dzięki temu nie trzeba śledzić tego kodu w Twoim nagłówku ani rysować oddzielnego diagramu. Dlatego w przypadku przerwania pracy mapy kodu ułatwiają odświeżenie pamięci o kodzie, nad którym pracujesz.

 ![Relacje mapy &#45; kodu mapy w kodzie](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")

 **Zielona strzałka pokazuje, gdzie znajduje się kursor w edytorze**

 Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można używać podczas pracy z mapami kodu, zobacz [przeglądanie i zmiana rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="understand-the-problem"></a>Omówienie problemu
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć usterkę, należy otworzyć rozwiązanie w programie Visual Studio i nacisnąć klawisz **F5** , aby rozpocząć debugowanie.

 Po narysowaniu linii i wybraniu **polecenia Cofnij moje ostatnie pociągnięcie**nic się nie dzieje, aż do rysowania następnego wiersza.

 ![Usterka &#45; Odtwórz mapy kodu](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")

 Aby rozpocząć badanie, Wyszukaj metodę `Undo`. Znajdziesz go w klasie `PaintCanvas`.

 ![Kod wyszukiwania &#45; mapy kodu](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")

## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu
 Teraz Rozpocznij mapowanie metody `undo` i jej relacji. W edytorze kodu należy dodać metodę `undo` i pola, do których się odwołuje, do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.

 ![Mapa &#45; kodu — Pokaż metodę i powiązane pola](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")

> [!TIP]
> Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zielona strzałka wskazuje pozycję kursora w kodzie. Strzałki między elementami reprezentują różne relacje. Aby uzyskać więcej informacji na temat elementów na mapie, przesuń wskaźnik myszy nad nich i zbadaj ich etykietki narzędzi.

 ![Pokaż etykietki narzędzi w mapie &#45; kodu](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")

## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy
 Aby zobaczyć definicję kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub zaznacz pole i naciśnij klawisz **F12**. Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.

 ![Definicja pola &#45; analizy mapy kodu](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")

 ![Definicja pola &#45; analizy mapy kodu](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")

> [!TIP]
> Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.

## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu
 Teraz chcesz wiedzieć, który inny kod współdziała z polami `history` i `paintObjects`. Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić z poziomu mapy lub z edytora kodu.

 ![Mapa &#45; kodu — Znajdź wszystkie odwołania](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")

 ![Otwieranie mapy kodu z poziomu edytora kodu](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")

> [!NOTE]
> Jeśli dodasz elementy z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklep Windows, wówczas te elementy zawsze pojawiają się z aktualnie aktywnym projektem aplikacji na mapie. Dlatego jeśli zmienisz kontekst na inny projekt aplikacji, kontekst na mapie również zmieni się dla wszystkich nowo dodanych elementów z projektu udostępnionego. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.

 ![Układ zmiany &#45; mapy kodu](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")

> [!TIP]
> Domyślnie opcja **Układ przyrostowy** jest włączona. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby ponownie rozmieścić całą mapę przy każdym dodawaniu nowych elementów, wyłącz opcję **Układ przyrostowy**.

 ![Układ zmiany &#45; mapy kodu](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")

 Zbadajmy te metody. Na mapie kliknij dwukrotnie metodę **metodę PaintCanvas** lub wybierz tę metodę i naciśnij klawisz **F12**. Dowiesz się, że ta metoda tworzy `history` i `paintObjects` jako puste listy.

 ![Definicja metody &#45; analizy mapy kodu](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")

 Teraz Powtórz te same kroki, aby przejrzeć definicję metody `clear`. Dowiesz się, że `clear` wykonuje kilka zadań z `paintObjects` i `history`. Następnie wywołuje metodę `Repaint`.

 ![Definicja metody &#45; analizy mapy kodu](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")

 Teraz sprawdź definicję metody `addPaintObject`. Wykonuje również pewne zadania z `history` i `paintObjects`. Wywołuje również `Repaint`.

 ![Definicja metody &#45; analizy mapy kodu](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")

## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy
 Wydaje się, że wszystkie metody, które modyfikują `history` i `paintObjects` wywołania `Repaint`. Jeszcze Metoda `undo` nie wywołuje `Repaint`, mimo że `undo` modyfikuje te same pola. Dlatego możesz rozwiązać ten problem, wywołując `Repaint` z `undo`.

 ![Mapa &#45; kodu nie znaleziono brakującego wywołania metody](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")

 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.

## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.

 ![Komentarz mapy &#45; kodu i flagi elementów do powstawania](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")

 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.

 ![Mapa &#45; kodu z komentarzem i oflagowanymi elementami](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")

 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.

 ![Udział mapy &#45; kodu, eksport, poczta](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")

## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione
 Aby naprawić ten błąd, należy dodać wywołanie `Repaint` do `undo`.

 ![Mapa &#45; kodu Dodaj brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")

 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie opcji **Cofnij ostatnie pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza, że wprowadzono poprawną poprawkę.

 ![Mapa &#45; kodu potwierdzenie usunięcia kodu](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")

 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.

 ![Mapa aktualizacji &#45; mapy kodu z brakującym wywołaniem metody](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")

 Mapa zawiera teraz link między **poleceniami Cofnij** i **odświeżenia**.

 ![Mapa kodu &#45; została zaktualizowana z wywołaniem metody](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")

> [!NOTE]
> Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.

 Dochodzenie zostało zakończone. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.

## <a name="see-also"></a>Zobacz też
 [Mapuj metody na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) [kodu wizualizacji](../modeling/visualize-code.md)
