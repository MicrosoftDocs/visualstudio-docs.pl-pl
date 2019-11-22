---
title: Metody mapowania dla stosu wywołań podczas debugowania
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3ddf45a48f6b9d8a5ac8155012f168703c67aa3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300779"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Metody mapowania dla stosu wywołań podczas debugowania w programie Visual Studio.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Można robić notatki na mapie, żeby śledzić, jak zachowuje się kod, przez co można skoncentrować się na wyszukiwaniu błędów.

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Potrzebne będą:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Kod, który można debugować, taki jak Visual C# .NET, Visual Basic .NET, C++, JavaScript lub X ++

  Zobacz: [film wideo: debugowanie wizualne za pomocą integracji debugera mapy kodu (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [Mapuj stos wywołań](#MapStack) • [robienie notatek dotyczących kodu](#MakeNotes) • [aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap) • [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode) • [znajdowanie błędów za pomocą mapy](#FindBugs) • [pytań i odpowiedzi](#QA)

  Szczegóły poleceń i akcji, można użyć podczas pracy z mapami kodu można znaleźć [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Mapuj stos wywołań

1. Rozpocznij debugowanie. (Klawiatura: **F5**)

2. Po skopiowaniu aplikacja przejdzie do trybu podziału lub wkroczysz do funkcji, wybierz **mapy kodu**. (Klawiatura: **Ctrl** + **Shift** +  **`** )

     ![Wybierz pozycję Mapa kodu, aby rozpocząć mapowanie stosu wywołań](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

     ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Mapa automatycznie zaktualizuje przerywając debugowania. Zobacz [aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap).

## <a name="MakeNotes"></a> Robienie notatek dotyczących kodu
 Dodaj komentarze, aby śledzić, co się dzieje w kodzie. Aby dodać nowy wiersz w komentarzu, naciśnij **Shift + Return**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aktualizacja mapy za pomocą następnego stosu wywołań
 Uruchom aplikację do następnego punktu przerwania lub wejścia do funkcji. Mapa dodaje nowy stos wywołań.

 ![Aktualizowanie mapy kodu przy użyciu następnego stosu wywołań](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Dodawanie kodu pokrewnego do mapy
 Teraz masz mapę — co dalej? Jeśli pracujesz z programem Visual C# .NET lub Visual Basic .NET, dodaj elementy, takie jak pola, właściwości i inne metody, aby śledzić, co dzieje się w kodzie.

 Kliknij dwukrotnie metodę, aby zobaczyć jej definicję kodu lub użyć menu skrótów dla metody. (Klawiatura: Wybierz metodę na mapie i naciśnij klawisz **F12**)

 ![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Dodaj elementy, które chcesz śledzić na mapie.

 ![Pokaż pola w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Domyślnie Dodawanie elementów do mapy dodaje również węzły nadrzędne grupy, takie jak klasy, przestrzeni nazw i zestawu. Gdy jest to przydatne, można zachować mapy prostego przez wyłączenie tej funkcji przy użyciu **obejmują elementy nadrzędne** przycisk na pasku narzędzi Mapa lub naciskając **CTRL** podczas dodawania elementów.

 ![Pola związane z metodą na mapie kodu stosu wywołań](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 W tym miejscu można łatwo zobaczyć, które metody wykorzystują te same pola. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

 Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: Mapa kodu stosu wywołań](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody używające pola na mapie kodu stosu wywołań](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Znajdowanie błędów za pomocą mapy
 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Na przykład załóżmy, że analizujesz błąd w programie rysunkowym. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Aby ustawić punkty przerwania `clear`, `undo`, i `Repaint` metod, rozpocząć debugowanie i utworzyć mapę podobną do tego:

 ![Dodawanie kolejnego stosu wywołań do mapy kodu](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Należy zauważyć, że wszystkie gesty użytkownika na mapie wywołują `Repaint`, z wyjątkiem `undo`. To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji działania programu, mapa dodaje nowe wywołanie z `undo` do `Repaint`:

 ![Dodaj nowe wywołanie metody do stosu wywołań na mapie kodu](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> PYTANIA I ODPOWIEDZI

- **Nie wszystkie wywołania są wyświetlane na mapie. Zalet?**

   Domyślnie tylko Twój własny kod pojawia się na mapie. Aby wyświetlić kod zewnętrzny, włącz go w **stos wywołań** okna:

   ![Wyświetlanie kodu zewnętrznego przy użyciu okna stosu wywołań](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   lub wyłącz **Włącz tylko mój kod** w opcjach debugowania Visual Studio:

   ![Pokaż kod zewnętrzny przy użyciu okna dialogowego opcji](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Zmiana mapy wpływa na kod?**

   Zmiana na mapie w żaden sposób nie wpływa na kod. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

- **Co oznacza komunikat: "diagram może opierać się na starszej wersji kodu"?**

   Kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

- **Jak kontrolować układ mapy?**

   Otwórz **układ** menu na pasku narzędzi Mapa:

  - Zmiana układu domyślnego.

  - Aby zatrzymać automatyczne rozmieszczanie na mapie, należy wyłączyć opcję **automatycznie rozmieszczaj podczas debugowania**.

  - Aby zmienić kolejność możliwie mapy, podczas dodawania elementów, należy wyłączyć opcję **układ Przyrostowy**.

- **Czy można dzielić się mapami w innym osobom?**

   Można eksportować mapę, przesłać ją do innych osób, o ile posiada się Microsoft Outlook, albo zapisać jako swoje rozwiązanie, żeby można je było zaewidencjonować w kontroli wersji Team Foundation.

   ![Udostępnianie mapy kodu stosu wywołań innym osobom](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Jak zatrzymać automatyczne dodawanie nowych stosów wywołań do mapy?**

   Wybierz ![przycisk &#45; Pokaż automatycznie umieszczane na mapie kodu](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") na pasku narzędzi mapy. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij klawisz **Ctrl** + **Shift** +  **`** .

   Mapa nadal będzie wyróżniać istniejące stosy wywołań na mapie, którą debugujesz.

- **Co ikony elementów i strzałki oznaczają?**

   Aby uzyskać więcej informacji na temat elementu, umieść kursor myszy nad nią i przyjrzyj się etykietka narzędzia elementu. Można również przeglądać **legendy** Aby dowiedzieć się, co oznacza każda ikona.

   ![Co oznaczają ikony na mapie kodu stosu wywołań?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Zobacz: [Mapuj stos wywołań](#MapStack) • [robienie notatek dotyczących kodu](#MakeNotes) • [aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap) • [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode) • [ Znajdowanie błędów za pomocą mapy](#FindBugs)

## <a name="see-also"></a>Zobacz też
 [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) [mapy Użyj kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md) [Znajdź potencjalne problemy przy użyciu kodu mapy analizatory](../modeling/find-potential-problems-using-code-map-analyzers.md) [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md)
