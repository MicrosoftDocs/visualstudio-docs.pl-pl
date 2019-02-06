---
title: Metody mapowania dla stosu wywołań podczas debugowania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdad61c5edc40dc752f52dcfa79227a5865b8aff
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55767792"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Metody mapowania dla stosu wywołań podczas debugowania w programie Visual Studio.
Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Można robić notatki na mapie, żeby śledzić, jak zachowuje się kod, przez co można skoncentrować się na wyszukiwaniu błędów.

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap_overview.png)

 Będą potrzebne:

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

- Kod, który można debugować, taki jak Visual C#, Visual Basic, C++, JavaScript lub X ++

  Zobacz:

- [Wideo: Wizualne debugowanie dzięki integracji debugera mapy kodu (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

- [Mapuj stos wywołań](#MapStack)

- [Robienie notatek dotyczących kodu](#MakeNotes)

- [Aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap)

- [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode)

- [Znajdowanie błędów za pomocą mapy](#FindBugs)

- [PYTANIA I ODPOWIEDZI](#QA)

  Szczegóły poleceń i akcji, można użyć podczas pracy z mapami kodu można znaleźć [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Mapuj stos wywołań

1.  Rozpocznij debugowanie. (Klawiatura: **F5**)

2.  Po skopiowaniu aplikacja przejdzie do trybu podziału lub wkroczysz do funkcji, wybierz **mapy kodu**. (Klawiatura: **Ctrl** + **Shift** + **`**)

     ![Wybierz mapę kodu, aby rozpocząć mapowanie stosu wywołań](../debugger/media/debuggermap_choosecodemap.png)

     Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

     ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap_seeundocallstack.png)

     Mapa automatycznie zaktualizuje przerywając debugowania. Zobacz [aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap).

## <a name="MakeNotes"></a> Robienie notatek dotyczących kodu
 Dodaj komentarze, aby śledzić, co się dzieje w kodzie. Aby dodać nowy wiersz w komentarzu, naciśnij **Shift + Return**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a> Aktualizacja mapy za pomocą następnego stosu wywołań
 Uruchom aplikację do następnego punktu przerwania lub wejścia do funkcji. Mapa dodaje nowy stos wywołań.

 ![Aktualizuj mapę kodu za pomocą następnego stosu wywołań](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a> Dodawanie kodu pokrewnego do mapy
 Teraz masz mapę — co dalej? Jeśli pracujesz w języku C# lub Visual Basic, należy dodać elementy, takie jak pola, właściwości i innych metod, aby śledzić, co się dzieje w kodzie.

 Kliknij dwukrotnie metodę, aby zobaczyć jej definicję kodu lub użyć menu skrótów dla metody. (Klawiatura: Wybierz metodę na mapie i naciśnij klawisz **F12**)

 ![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap_gotocodedefinition.png)

 Dodaj elementy, które chcesz śledzić na mapie.

 ![Pokazywanie pól w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
>  Domyślnie Dodawanie elementów do mapy dodaje również węzły nadrzędne grupy, takie jak klasy, przestrzeni nazw i zestawu. Gdy jest to przydatne, można zachować mapy prostego przez wyłączenie tej funkcji przy użyciu **obejmują elementy nadrzędne** przycisk na pasku narzędzi Mapa lub naciskając **CTRL** podczas dodawania elementów.

 ![Pola powiązane z metodę na mapie kodu stosu wywołań](../debugger/media/debuggermap_showedfields.png)

 W tym miejscu można łatwo zobaczyć, które metody wykorzystują te same pola. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

 Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: mapy kodu stosu wywołań](../debugger/media/debuggermap_findallreferences.png)

 ![Metody używające pole na mapie kodu stosu wywołań](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a> Znajdowanie błędów za pomocą mapy
 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Na przykład załóżmy, że analizujesz błąd w programie rysunkowym. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Aby ustawić punkty przerwania `clear`, `undo`, i `Repaint` metod, rozpocząć debugowanie i utworzyć mapę podobną do tego:

 ![Dodaj inny stos wywołań do mapy kodu](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Należy zauważyć, że wszystkie gesty użytkownika na mapie wywołują `Repaint`, z wyjątkiem `undo`. To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji działania programu, mapa dodaje nowe wywołanie z `undo` do `Repaint`:

 ![Dodaj nowy stos wywołań do wywołania metody na mapie kodu](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a> PYTANIA I ODPOWIEDZI

- **Nie wszystkie wywołania są wyświetlane na mapie. Dlaczego?**

   Domyślnie tylko Twój własny kod pojawia się na mapie. Aby wyświetlić kod zewnętrzny, włącz go w **stos wywołań** okna:

   ![Wyświetlić kod zewnętrzny, w oknie stosu wywołań](../debugger/media/debuggermap_callstackmenu.png)

   lub wyłącz **Włącz tylko mój kod** w opcjach debugowania Visual Studio:

   ![Pokaż kod zewnętrzny, za pomocą okna dialogowego Opcje](../debugger/media/debuggermap_debugoptions.png)

- **Zmiana mapy wpływa na kod?**

   Zmiana na mapie nie ma wpływu na kod w dowolny sposób. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

- **Co oznacza komunikat: "Diagram może opierać się na starszej wersji kodu"?**

   Kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

- **Jak kontrolować układ mapy?**

   Otwórz **układ** menu na pasku narzędzi Mapa:

  -   Zmiana układu domyślnego.

  -   Aby zatrzymać automatyczne rozmieszczanie na mapie, należy wyłączyć opcję **automatycznie rozmieszczaj podczas debugowania**.

  -   Aby zmienić kolejność możliwie mapy, podczas dodawania elementów, należy wyłączyć opcję **układ Przyrostowy**.

- **Czy można dzielić się mapami w innym osobom?**

   Można eksportować mapę, wysyłania do innych osób, jeśli program Microsoft Outlook lub zapisać go do rozwiązania, dzięki czemu można je było zaewidencjonować w kontroli źródła.

   ![Mapy kodu stosu wywołań udostępniania innym osobom](../debugger/media/debuggermap_sharewithothers.png)

- **Jak zatrzymać automatyczne dodawanie nowych stosów wywołań do mapy?**

   Wybierz ![przycisk &#45; Pokaż automatycznie umieszczane na mapie kodu](../debugger/media/debuggermap_automaticupdateicon.gif) na pasku narzędzi mapy. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij klawisz **Ctrl** + **Shift** + **`**.

   Mapa nadal będzie wyróżniać istniejące stosy wywołań na mapie, którą debugujesz.

- **Co ikony elementów i strzałki oznaczają?**

   Aby uzyskać więcej informacji na temat elementu, umieść kursor myszy nad nią i przyjrzyj się etykietka narzędzia elementu. Można również przeglądać **legendy** Aby dowiedzieć się, co oznacza każda ikona.

   ![Co oznaczają ikony na mapie kodu stosu wywołań](../debugger/media/debuggermap_showlegend.png)

  Zobacz:

- [Mapuj stos wywołań](#MapStack)

- [Robienie notatek dotyczących kodu](#MakeNotes)

- [Aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap)

- [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode)

- [Znajdowanie błędów za pomocą mapy](#FindBugs)

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
