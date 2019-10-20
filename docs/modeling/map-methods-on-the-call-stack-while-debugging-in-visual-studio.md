---
title: Metody mapowania dla stosu wywołań podczas debugowania
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c294ce3c6dcf3a880cf5f57ca825064366e08e2b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668229"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Metody mapowania dla stosu wywołań podczas debugowania w programie Visual Studio.

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Można robić notatki na mapie, żeby śledzić, jak zachowuje się kod, przez co można skoncentrować się na wyszukiwaniu błędów.

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap_overview.png)

 Będziesz potrzebować:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Kod, który możesz debugować, taki jak Visual C#, Visual Basic, C++, JavaScript lub X + +

  Zobacz:

- [Wideo: Debuguj wizualnie dzięki integracji z debugerem mapy kodu (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

- [Mapowanie stosu wywołań](#MapStack)

- [Utwórz notatki dotyczące kodu](#MakeNotes)

- [Aktualizowanie mapy za pomocą następnego stosu wywołań](#UpdateMap)

- [Dodaj kod pokrewny do mapy](#AddRelatedCode)

- [Znajdowanie usterek przy użyciu mapy](#FindBugs)

- [p & A](#QA)

  Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można używać podczas pracy z mapami kodu, zobacz [przeglądanie i zmiana rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a>Mapowanie stosu wywołań

1. Rozpocznij debugowanie. (Klawiatura: **F5**)

2. Gdy aplikacja przejdzie w tryb przerwania lub przejdziesz do funkcji, wybierz pozycję **Mapa kodu**. (Klawiatura: **Ctrl**  + **SHIFT**  +  **`** )

     ![Wybierz pozycję Mapa kodu, aby rozpocząć mapowanie stosu wywołań](../debugger/media/debuggermap_choosecodemap.png)

     Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

     ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap_seeundocallstack.png)

     Mapa zostanie automatycznie zaktualizowana podczas kontynuowania debugowania. Zobacz [Aktualizowanie mapy za pomocą następnego stosu wywołań](#UpdateMap).

## <a name="MakeNotes"></a>Utwórz notatki dotyczące kodu

 Dodaj komentarze, aby śledzić, co się dzieje w kodzie. Aby dodać nowy wiersz w komentarzu, naciśnij klawisze **Shift + Return**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a>Aktualizowanie mapy za pomocą następnego stosu wywołań

 Uruchom aplikację do następnego punktu przerwania lub wejścia do funkcji. Mapa dodaje nowy stos wywołań.

 ![Aktualizowanie mapy kodu przy użyciu następnego stosu wywołań](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a>Dodaj kod pokrewny do mapy

 Teraz masz mapę — co dalej? Jeśli pracujesz z programem C# lub Visual Basic, Dodaj elementy, takie jak pola, właściwości i inne metody, aby śledzić, co się dzieje w kodzie.

 Kliknij dwukrotnie metodę, aby zobaczyć jej definicję kodu, lub użyj menu skrótów dla metody. (Klawiatura: Wybierz metodę na mapie, a następnie naciśnij klawisz **F12**)

 ![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap_gotocodedefinition.png)

 Dodaj elementy, które chcesz śledzić na mapie.

 ![Pokaż pola w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Domyślnie Dodawanie elementów do mapy powoduje również dodanie węzłów grupy nadrzędnej, takich jak Klasa, przestrzeń nazw i zestaw. Chociaż jest to przydatne, można zachować mapę prostą, wyłączając tę funkcję przy użyciu przycisku **Dołącz rodziców** na pasku narzędzi mapy lub naciskając klawisz **Ctrl** podczas dodawania elementów.

 ![Pola związane z metodą na mapie kodu stosu wywołań](../debugger/media/debuggermap_showedfields.png)

 W tym miejscu można łatwo zobaczyć, które metody wykorzystują te same pola. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

 Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: Mapa kodu stosu wywołań](../debugger/media/debuggermap_findallreferences.png)

 ![Metody używające pola na mapie kodu stosu wywołań](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a>Znajdowanie usterek przy użyciu mapy

 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Załóżmy na przykład, że badasz usterkę w programie do rysowania. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Dlatego należy ustawić punkty przerwania w metodach `clear`, `undo` i `Repaint`, rozpocząć debugowanie i utworzyć mapę podobną do tej:

 ![Dodawanie kolejnego stosu wywołań do mapy kodu](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Zauważ, że wszystkie gesty użytkownika na mapie `Repaint`, z wyjątkiem `undo`. To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji działania programu, Mapa dodaje nowe wywołanie z `undo` do `Repaint`:

 ![Dodaj nowe wywołanie metody do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a>p & A

- **Nie wszystkie wywołania są wyświetlane na mapie. Zalet?**

   Domyślnie tylko własny kod jest wyświetlany na mapie. Aby wyświetlić kod zewnętrzny, włącz go w oknie **stosu wywołań** :

   ![Wyświetlanie kodu zewnętrznego przy użyciu okna stosu wywołań](../debugger/media/debuggermap_callstackmenu.png)

   lub wyłącz opcję **włącz tylko mój kod** w opcjach debugowania programu Visual Studio:

   ![Pokaż kod zewnętrzny przy użyciu okna dialogowego opcji](../debugger/media/debuggermap_debugoptions.png)

- **Czy zmiana mapy ma wpływ na kod?**

   Zmiana mapy nie ma wpływu na kod. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

- **Co oznacza komunikat: "diagram może opierać się na starszej wersji kodu"?**

   Kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

- **Jak mogę kontrolować układ mapy?**

   Otwórz menu **Układ** na pasku narzędzi Mapa:

  - Zmiana układu domyślnego.

  - Aby zatrzymać automatyczne rozmieszczanie mapy, należy wyłączyć **Automatyczne układ podczas debugowania**.

  - Aby zmienić rozmieszczenie mapy możliwie najbliżej podczas dodawania elementów, należy wyłączyć opcję **Układ przyrostowy**.

- **Czy mogę udostępnić mapę innym osobom?**

   Możesz wyeksportować mapę, wysłać ją do innych osób, jeśli masz program Microsoft Outlook lub zapisać ją w rozwiązaniu, aby można było ją sprawdzić w kontroli źródła.

   ![Udostępnianie mapy kodu stosu wywołań innym osobom](../debugger/media/debuggermap_sharewithothers.png)

- **Jak mogę zatrzymać automatyczne dodawanie nowych stosów wywołań przez mapę?**

   Wybierz ![Button &#45; Pokaż stos wywołań na mapie kodu automatycznie ](../debugger/media/debuggermap_automaticupdateicon.gif) na pasku narzędzi Mapa. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij **klawisze Ctrl**  + **SHIFT**  +  **`** .

   Mapa będzie nadal wyróżniać istniejące stosy wywołań na mapie podczas debugowania.

- **Co oznaczają ikony elementów i strzałki?**

   Aby uzyskać więcej informacji na temat elementu, przesuń wskaźnik myszy nad nim i poszukaj etykietki narzędzia elementu. Możesz również przyjrzeć się **legendzie** , aby dowiedzieć się, co oznacza każda ikona.

   ![Co oznaczają ikony na mapie kodu stosu wywołań?](../debugger/media/debuggermap_showlegend.png)

  Zobacz:

- [Mapowanie stosu wywołań](#MapStack)

- [Utwórz notatki dotyczące kodu](#MakeNotes)

- [Aktualizowanie mapy za pomocą następnego stosu wywołań](#UpdateMap)

- [Dodaj kod pokrewny do mapy](#AddRelatedCode)

- [Znajdowanie usterek przy użyciu mapy](#FindBugs)

## <a name="see-also"></a>Zobacz także

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
