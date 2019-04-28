---
title: Używanie map kodu do debugowania aplikacji | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b7f446d2c9a1b22488746eff9ba04044d2621013
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439672"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapy kodu może pomóc uniknąć zagubienia w dużych bazach kodu, w nieznanym kodzie lub starszego kodu. Na przykład podczas debugowania możesz chcieć spojrzeć na kod w wielu plikach i projektach. Używanie map kodu do poruszania się fragmentów kodu i zrozumienie relacji między nimi. Dzięki temu nie trzeba informacji o ten kod w głowie lub narysować diagram oddzielnych. Tak gdy działanie zostanie zakłócone swoją pracę, mapy kodu pomogą odświeżyć sobie pamięć o kodzie, nad którymi pracuje.  
  
 ![Mapy kodu &#45; mapę relacji w kodzie](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Pokazuje zielona strzałka, gdy kursor jest wyświetlany w edytorze**  
  
 Szczegóły poleceń i akcji, można użyć podczas pracy z mapami kodu można znaleźć [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).  
  
## <a name="understand-the-problem"></a>Omówienie problemu  
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć błąd, otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz **F5** można rozpocząć debugowania.  
  
 Po narysowaniu linii i wybraniu **Cofnij Moje ostatnie pociągnięcie**, aż do rysowania następnej linii nic się nie dzieje.  
  
 ![Mapy kodu &#45; odtworzenia usterki](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Tak więc zaczynasz dochodzenie od wyszukania `Undo` metody. Możesz znaleźć `PaintCanvas` klasy.  
  
 ![Mapy kodu &#45; wyszukiwanie kodu](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu  
 Teraz rozpocząć mapowanie `undo` metody i relacje. W edytorze kodu Dodaj `undo` metody i pola, które odwołuje się do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.  
  
 ![Mapy kodu &#45; Pokaż metody i powiązanych pól](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
> Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zielona strzałka wskazuje pozycję kursora w kodzie. Strzałki między elementami reprezentują różne relacje. Przesuwanie wskaźnika myszy nad nimi, a następnie badanie ich etykietki narzędzi, można uzyskać więcej informacji o elementach na mapie.  
  
 ![Mapy kodu &#45; pokazuje etykietki narzędzi](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy  
 Aby zobaczyć definicję kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub wybierz pole i naciśnij klawisz **F12**. Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.  
  
 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
> Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.  
  
## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu  
 Teraz chcesz wiedzieć, który inny kod współdziała z `history` i `paintObjects` pola. Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić z mapy albo z poziomu edytora kodu.  
  
 ![Mapy kodu &#45; Znajdź wszystkie odwołania](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Otwórz mapę kodów z edytora kodu](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
> Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Windows Store, a następnie te elementy zawsze pojawiają się z projektem aktualnie aktywnych aplikacji na mapie. Dlatego jeśli zmienić kontekst do innego projektu aplikacji, a następnie zmienia także kontekst na mapie dla dowolnego nowo dodane elementy z udostępnionego projektu. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.  
  
 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.  
  
 ![Mapy kodu &#45; Zmień układ](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
> Domyślnie **układ Przyrostowy** jest włączona. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby zreorganizować całą mapę przy każdym dodawaniu nowych elementów, należy wyłączyć opcję **układ Przyrostowy**.  
  
 ![Mapy kodu &#45; Zmień układ](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Zbadajmy te metody. Na mapie, kliknij dwukrotnie **PaintCanvas** metodę, lub wybierz tę metodę i naciśnij klawisz **F12**. Dowiedz się, że ta metoda tworzy `history` i `paintObjects` jako puste listy.  
  
 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Teraz Powtórz te same kroki, aby zbadać `clear` definicję metody. Możesz dowiedzieć się, że `clear` wykonuje pewne zadania z `paintObjects` i `history`. Następnie wywołuje `Repaint` metody.  
  
 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Teraz zbadaj `addPaintObject` definicję metody. Wykonuje także niektóre zadania za pomocą `history` i `paintObjects`. Wzywa także `Repaint`.  
  
 ![Mapy kodu &#45; zbadać definicję metody](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy  
 Wydaje się, że wszystkie metody, które modyfikują `history` i `paintObjects` wywołania `Repaint`. Jeszcze `undo` nie wywołuje metody `Repaint`, nawet jeśli `undo` modyfikuje te same pola. Dlatego uważasz, że możesz rozwiązać ten problem, wywołując `Repaint` z `undo`.  
  
 ![Mapy kodu &#45; Znajdź brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.  
  
## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki  
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.  
  
 ![Mapy kodu &#45; komentarz i flagować elementy monitującą](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.  
  
 ![Mapy kodu &#45; komentarzem z elementami oflagowanych](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.  
  
 ![Mapy kodu &#45; udziału, export, poczta](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione  
 Aby rozwiązać ten problem, należy dodać wywołanie dla `Repaint` do `undo`.  
  
 ![Mapy kodu &#45; Dodaj brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie **Cofnij Moje ostatnie pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza wykonane prawidłowej poprawki.  
  
 ![Mapy kodu &#45; poprawki kodu Potwierdź](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.  
  
 ![Mapy kodu &#45; mapy aktualizacji z brakującymi wywołania metody](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 Mapa obecnie pokazuje łącze między **Cofnij** i **Repaint**.  
  
 ![Mapy kodu &#45; mapy zaktualizowane przy użyciu wywołania metody](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
> Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.  
  
 Dochodzenie zostało zakończone. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.  
  
## <a name="see-also"></a>Zobacz też  
 [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
