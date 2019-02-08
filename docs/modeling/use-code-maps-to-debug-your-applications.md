---
title: Używanie map kodu do debugowania aplikacji
ms.date: 09/28/2018
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e421c65e83bca88c01ea58cfd5cc402c6011cb23
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934890"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji

Mapy kodu może pomóc uniknąć zagubienia w dużych bazach kodu, w nieznanym kodzie lub starszego kodu. Na przykład podczas debugowania, może być konieczne spojrzeć na kod w wielu plikach i projektach. Używanie map kodu do poruszania się fragmentów kodu i zrozumienie relacji między nimi. Dzięki temu nie trzeba informacji o ten kod w głowie lub narysować diagram oddzielnych. Tak gdy działanie zostanie zakłócone swoją pracę, mapy kodu pomogą odświeżyć sobie pamięć o kodzie, nad którymi pracuje.

![Mapy kodu &#45; mapę relacji w kodzie](../modeling/media/codemapstoryboardpaint.png)

**Pokazuje zielona strzałka, gdy kursor jest wyświetlany w edytorze**

Szczegóły poleceń i akcji, można użyć podczas pracy z mapami kodu można znaleźć [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Aby tworzyć i edytować map kodu, należy programu Visual Studio Enterprise edition. W Visual Studio Community i Professional może otwierać diagramy, które były generowane w wersji Enterprise edition, ale nie można ich edytować.

## <a name="understand-the-problem"></a>Omówienie problemu
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć błąd, otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz **F5** można rozpocząć debugowania.

 Po narysowaniu linii i wybraniu **Cofnij Moje ostatnie pociągnięcie**, aż do rysowania następnej linii nic się nie dzieje.

 ![Mapy kodu &#45; odtworzenia usterki](../modeling/media/codemapstoryboardpaint0.png)

 Tak więc zaczynasz dochodzenie od wyszukania `Undo` metody. Możesz znaleźć `PaintCanvas` klasy.

 ![Mapy kodu &#45; wyszukiwanie kodu](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu
 Teraz rozpocząć mapowanie `undo` metody i relacje. W edytorze kodu Dodaj `undo` metody i pola, które odwołuje się do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.

 ![Mapy kodu &#45; Pokaż metody i powiązanych pól](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zielona strzałka wskazuje pozycję kursora w kodzie. Strzałki między elementami reprezentują różne relacje. Przesuwanie wskaźnika myszy nad nimi, a następnie badanie ich etykietki narzędzi, można uzyskać więcej informacji o elementach na mapie.

 ![Mapy kodu &#45; pokazuje etykietki narzędzi](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy
 Aby zobaczyć definicję kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub wybierz pole i naciśnij klawisz **F12**. Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.

 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5.png)

 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.

## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu
 Teraz chcesz wiedzieć, który inny kod współdziała z `history` i `paintObjects` pola. Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić z mapy albo z poziomu edytora kodu.

 ![Mapy kodu &#45; Znajdź wszystkie odwołania](../modeling/media/codemapstoryboardpaint6.png)

 ![Otwórz mapę kodów z edytora kodu](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Windows Store, a następnie te elementy zawsze pojawiają się z projektem aktualnie aktywnych aplikacji na mapie. Dlatego jeśli zmienić kontekst do innego projektu aplikacji, a następnie zmienia także kontekst na mapie dla dowolnego nowo dodane elementy z udostępnionego projektu. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.

 ![Mapy kodu &#45; Zmień układ](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Domyślnie **układ Przyrostowy** jest włączona. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby zreorganizować całą mapę przy każdym dodawaniu nowych elementów, należy wyłączyć opcję **układ Przyrostowy**.

 ![Mapy kodu &#45; Zmień układ](../modeling/media/codemapstoryboardpaint7.png)

 Zbadajmy te metody. Na mapie, kliknij dwukrotnie **PaintCanvas** metodę, lub wybierz tę metodę i naciśnij klawisz **F12**. Dowiedz się, że ta metoda tworzy `history` i `paintObjects` jako puste listy.

 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint8.png)

 Teraz Powtórz te same kroki, aby zbadać `clear` definicję metody. Możesz dowiedzieć się, że `clear` wykonuje pewne zadania z `paintObjects` i `history`. Następnie wywołuje `Repaint` metody.

 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint9.png)

 Teraz zbadaj `addPaintObject` definicję metody. Wykonuje także niektóre zadania za pomocą `history` i `paintObjects`. Wzywa także `Repaint`.

 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy
 Wydaje się, że wszystkie metody, które modyfikują `history` i `paintObjects` wywołania `Repaint`. Jeszcze `undo` nie wywołuje metody `Repaint`, nawet jeśli `undo` modyfikuje te same pola. Dlatego uważasz, że możesz rozwiązać ten problem, wywołując `Repaint` z `undo`.

 ![Mapy kodu &#45; Znajdź brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint11.png)

 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.

## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.

 ![Mapy kodu &#45; komentarz i flagować elementy do monitowania](../modeling/media/codemapstoryboardpaint12.png)

 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.

 ![Mapy kodu &#45; komentarzem z elementami oflagowane](../modeling/media/codemapstoryboardpaint12a.png)

 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.

 ![Mapy kodu &#45; udziału, eksport, wiadomości e-mail](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione
 Aby rozwiązać ten problem, należy dodać wywołanie dla `Repaint` do `undo`.

 ![Mapy kodu &#45; Dodaj brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint14.png)

 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie **Cofnij Moje ostatnie pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza wykonane prawidłowej poprawki.

 ![Mapy kodu &#45; Potwierdź poprawki kodu](../modeling/media/codemapstoryboardpaint15.png)

 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.

 ![Mapy kodu &#45; mapy aktualizacji z brakującymi wywołania metody](../modeling/media/codemapstoryboardpaint16.png)

 Mapa obecnie pokazuje łącze między **Cofnij** i **Repaint**.

 ![Mapy kodu &#45; mapy zaktualizowane przy użyciu wywołania metody](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.

 Po zakończeniu badania. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.

## <a name="see-also"></a>Zobacz też

- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
