---
title: Używanie map kodu do debugowania aplikacji
description: Dowiedz się, jak używać map kodu, aby uniknąć zgubień w dużych bazach kodu, nieznanym kodzie lub starszym kodzie.
ms.custom: SEO-VS-2020
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b422c6c7857ca1baaa5bd1d8a7d6955e8b6751b3
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375802"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji

[Mapy kodu w Visual Studio](../modeling/map-dependencies-across-your-solutions.md) mogą pomóc uniknąć zgubień w dużych bazach kodu, nieznanym kodzie lub starszym kodzie. Na przykład podczas debugowania może być konieczne przyjrzenie się kodowi w wielu plikach i projektach. Mapy kodu mogą nawigować po fragmentach kodu i rozumiać relacje między nimi. Dzięki temu nie trzeba śledzić tego kodu w głowy ani rysować oddzielnego diagramu. Dlatego po przerwaniu pracy mapy kodu pomagają odświeżyć pamięć na temat kodu, nad którym pracujesz.

![Mapowanie kodu &#45; mapowanie relacji w kodzie](../modeling/media/codemapstoryboardpaint.png)

**Zielona strzałka wskazuje miejsce, w którym kursor pojawia się w edytorze**

Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można użyć podczas pracy z mapami kodu, zobacz Przeglądanie i zmiana [rozmieszczania map kodu](../modeling/browse-and-rearrange-code-maps.md).

Dowiedz się więcej na [temat debugowania Visual Studio użyciu narzędzia debugera](../debugger/debugger-feature-tour.md).

> [!NOTE]
> Aby tworzyć i edytować mapy kodu, musisz Visual Studio Enterprise wersji. W Visual Studio Community i Professional można otwierać diagramy wygenerowane w wersji Enterprise, ale nie można ich edytować.

## <a name="understand-the-problem"></a>Omówienie problemu
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć usterkę, otwórz rozwiązanie na stronie Visual Studio naciśnij **klawisz F5,** aby rozpocząć debugowanie.

 Po narysowaniu linii i wybraniu polecenia **Cofnij mój ostatni pociągnięcie** nic się nie dzieje do momentu narysowania następnego wiersza.

 ![Usterka repro &#45; mapy kodu](../modeling/media/codemapstoryboardpaint0.png)

 Zacznij więc badać, wyszukując `Undo` metodę . Znajdziesz go w `PaintCanvas` klasie .

 ![Mapa kodu &#45; znajdowanie kodu](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu
 Teraz rozpocznij mapowanie `undo` metody i jej relacji. W edytorze kodu dodajesz metodę i pola, do których się `undo` odwołuje, do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.

 ![Mapa kodu &#45; Pokazywanie metody i powiązanych pól](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zielona strzałka pokazuje położenie kursora w kodzie. Strzałki między elementami reprezentują różne relacje. Więcej informacji na temat elementów na mapie można uzyskać, przesuwając wskaźnik myszy nad nimi i sprawdzając ich etykietki narzędzi.

 ![Mapa kodu &#45; pokaż etykietki narzędzi](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy
 Aby wyświetlić definicję kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub wybierz pole i naciśnij **klawisz F12.** Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.

 ![Zrzut ekranu przedstawiający okno mapy kodu z wybranym polem historii i oknem edytora kodu, w którym wyróżnione są wszystkie wystąpienia historii.](../modeling/media/codemapstoryboardpaint5.png)

 ![Zrzut ekranu przedstawiający okno mapy kodu z wybranym polem paintObjects oraz okno edytora kodu, w którym wyróżnione są wszystkie wystąpienia obiektu paintObjects.](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.

## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu
 Teraz chcesz wiedzieć, który inny kod współdziała z `history` polami `paintObjects` i . Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić za pomocą mapy lub edytora kodu.

 ![Mapa kodu &#45; znajdowanie wszystkich odwołań](../modeling/media/codemapstoryboardpaint6.png)

 ![Otwieranie mapy kodu z edytora kodu](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Jeśli dodasz elementy z projektu, który jest udostępniany w wielu aplikacjach, takich jak Windows Phone lub Sklep Windows, te elementy są zawsze wyświetlane z aktualnie aktywnym projektem aplikacji na mapie. Jeśli więc zmienisz kontekst na inny projekt aplikacji, kontekst na mapie zmieni się również dla wszystkich nowo dodanych elementów z udostępnionego projektu. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.

 ![Zrzut ekranu przedstawiający okno mapy kodu z otwartym menu Układ i wybranym poleceniem Od lewej do Element.](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Domyślnie układ **przyrostowy** jest włączony. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby zmienić rozmieszczenie całej mapy za każdym razem, gdy dodajesz nowe elementy, wyłącz układ **przyrostowy**.

 ![Zrzut ekranu przedstawiający okno mapy kodu ze strzałkami relacji między polami, które wskazują od lewej do prawej.](../modeling/media/codemapstoryboardpaint7.png)

 Zbadajmy te metody. Na mapie kliknij dwukrotnie metodę **PaintCanvas** lub wybierz tę metodę i naciśnij **klawisz F12.** Dowiesz się, że ta metoda tworzy `history` listy i jako puste `paintObjects` listy.

 ![Zrzut ekranu przedstawiający okno mapy kodu z wybraną metodą PaintCanvas i obraz fragmentu kodu przedstawiający wyróżnione nazwy metody PainCanvas.](../modeling/media/codemapstoryboardpaint8.png)

 Teraz powtórz te same kroki, aby zbadać `clear` definicję metody. Dowiesz się, `clear` że program wykonuje niektóre zadania za pomocą i `paintObjects` `history` . Następnie wywołuje metodę `Repaint` .

 ![Zrzut ekranu przedstawiający okno mapy kodu z wybraną metodą Clear oraz obraz fragmentu kodu przedstawiający kod metody Clear.](../modeling/media/codemapstoryboardpaint9.png)

 Teraz przeanalizuj `addPaintObject` definicję metody. Wykonuje również niektóre zadania z i `history` `paintObjects` . Wywołuje również `Repaint` .

 ![Zrzut ekranu przedstawiający okno mapy kodu z wybraną metodą addPaintObject i obraz fragmentu kodu przedstawiający kod metody addPaintObject.](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy
 Wygląda na to, że wszystkie metody modyfikujące i `history` `paintObjects` wywołujące . `Repaint` Jednak `undo` metoda nie wywoła metody `Repaint` , mimo `undo` że modyfikuje te same pola. Uważasz więc, że możesz rozwiązać ten problem, wywołując `Repaint` wywołanie z `undo` .

 ![Mapowanie kodu &#45; znalezienie brakującego wywołania metody](../modeling/media/codemapstoryboardpaint11.png)

 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.

## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.

 ![Mapa kodu &#45; elementy komentarza i flagi do obserwowania](../modeling/media/codemapstoryboardpaint12.png)

 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.

 ![Mapa kodu &#45; z komentarzami i oflagowanych elementów](../modeling/media/codemapstoryboardpaint12a.png)

 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.

 ![Mapa kodu &#45; udostępnianie, eksportowanie, poczta](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione
 Aby naprawić tę usterkę, należy dodać wywołanie dla `Repaint` do `undo` .

 ![Mapa kodu &#45; dodanie brakującego wywołania metody](../modeling/media/codemapstoryboardpaint14.png)

 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie polecenia **Cofnij mój ostatni pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza, że poprawka jest poprawna.

 ![Mapa kodu &#45; potwierdź poprawkę kodu](../modeling/media/codemapstoryboardpaint15.png)

 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.

 ![Mapa kodu &#45; zaktualizować mapę z brakującym wywołaniem metody](../modeling/media/codemapstoryboardpaint16.png)

 Mapa zawiera teraz połączenie między poleceniem **cofania** **i poleceniem Cofnij.**

 ![Mapa kodu &#45; zaktualizowana mapa za pomocą wywołania metody](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.

 Teraz badanie zostało już wykonane. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.

## <a name="see-also"></a>Zobacz też

- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
