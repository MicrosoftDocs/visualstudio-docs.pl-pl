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
ms.openlocfilehash: 2e8376884f72aeca2f3bf56f0d7bbc1636379a18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847306"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Metody mapowania dla stosu wywołań podczas debugowania w programie Visual Studio.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Można robić notatki na mapie, żeby śledzić, jak zachowuje się kod, przez co można skoncentrować się na wyszukiwaniu błędów.

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Potrzebne będą:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Kod, który możesz debugować, taki jak Visual C# .NET, Visual Basic .NET, C++, JavaScript lub X + +

  Zobacz: [wideo: debugowanie wizualne za pomocą integracji z debugerem mapy kodu (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • [Mapowanie stosu wywołań](#MapStack) • [Tworzenie notatek dotyczących kodu](#MakeNotes) • [Aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap) • [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode) • [Znajdowanie błędów za pomocą mapy](#FindBugs) • [Q & A](#QA)

  Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można używać podczas pracy z mapami kodu, zobacz [przeglądanie i zmiana rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Mapowanie stosu wywołań

1. Uruchom debugowanie. (Klawiatura: **F5**)

2. Gdy aplikacja przejdzie w tryb przerwania lub przejdziesz do funkcji, wybierz pozycję **Mapa kodu**. (Klawiatura: **Ctrl**  +  **SHIFT**  +  **`** )

     ![Wybierz pozycję Mapa kodu, aby rozpocząć mapowanie stosu wywołań](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

     ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Mapa zostanie automatycznie zaktualizowana podczas kontynuowania debugowania. Zobacz [Aktualizowanie mapy za pomocą następnego stosu wywołań](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Utwórz notatki dotyczące kodu
 Dodaj komentarze, aby śledzić, co się dzieje w kodzie. Aby dodać nowy wiersz w komentarzu, naciśnij klawisze **Shift + Return**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Aktualizowanie mapy za pomocą następnego stosu wywołań
 Uruchom aplikację do następnego punktu przerwania lub wejścia do funkcji. Mapa dodaje nowy stos wywołań.

 ![Aktualizowanie mapy kodu przy użyciu następnego stosu wywołań](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Dodaj kod pokrewny do mapy
 Teraz masz mapę — co dalej? Jeśli pracujesz z programem Visual C# .NET lub Visual Basic .NET, dodaj elementy, takie jak pola, właściwości i inne metody, aby śledzić, co dzieje się w kodzie.

 Kliknij dwukrotnie metodę, aby zobaczyć jej definicję kodu, lub użyj menu skrótów dla metody. (Klawiatura: Wybierz metodę na mapie, a następnie naciśnij klawisz **F12**)

 ![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Dodaj elementy, które chcesz śledzić na mapie.

 ![Pokaż pola w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Domyślnie Dodawanie elementów do mapy powoduje również dodanie węzłów grupy nadrzędnej, takich jak Klasa, przestrzeń nazw i zestaw. Chociaż jest to przydatne, można zachować mapę prostą, wyłączając tę funkcję przy użyciu przycisku **Dołącz rodziców** na pasku narzędzi mapy lub naciskając klawisz **Ctrl** podczas dodawania elementów.

 ![Pola związane z metodą na mapie kodu stosu wywołań](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 W tym miejscu można łatwo zobaczyć, które metody wykorzystują te same pola. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

 Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: Mapa kodu stosu wywołań](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody używające pola na mapie kodu stosu wywołań](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Znajdowanie usterek przy użyciu mapy
 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Na przykład załóżmy, że analizujesz błąd w programie rysunkowym. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Dlatego należy ustawić punkty przerwania w `clear` `undo` metodach,, i `Repaint` , rozpocząć debugowanie i utworzyć mapę podobną do tej:

 ![Dodawanie kolejnego stosu wywołań do mapy kodu](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Zauważ, że wszystkie gesty użytkownika na mapie są wywoływane `Repaint` , z wyjątkiem `undo` . To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji działania programu, Mapa dodaje nowe wywołanie z `undo` do `Repaint` :

 ![Dodaj nowe wywołanie metody do stosu wywołań na mapie kodu](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="q--a"></a><a name="QA"></a> P & A

- **Nie wszystkie wywołania są wyświetlane na mapie. Zalet?**

   Domyślnie tylko własny kod jest wyświetlany na mapie. Aby wyświetlić kod zewnętrzny, włącz go w oknie **stosu wywołań** :

   ![Wyświetlanie kodu zewnętrznego przy użyciu okna stosu wywołań](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   lub wyłącz opcję **włącz tylko mój kod** w opcjach debugowania programu Visual Studio:

   ![Pokaż kod zewnętrzny przy użyciu okna dialogowego opcji](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Czy zmiana mapy ma wpływ na kod?**

   Zmiana na mapie w żaden sposób nie wpływa na kod. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

- **Co oznacza komunikat: "diagram może opierać się na starszej wersji kodu"?**

   Kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

- **Jak mogę kontrolować układ mapy?**

   Otwórz menu **Układ** na pasku narzędzi Mapa:

  - Zmiana układu domyślnego.

  - Aby zatrzymać automatyczne rozmieszczanie mapy, należy wyłączyć **Automatyczne układ podczas debugowania**.

  - Aby zmienić rozmieszczenie mapy możliwie najbliżej podczas dodawania elementów, należy wyłączyć opcję **Układ przyrostowy**.

- **Czy mogę udostępnić mapę innym osobom?**

   Można eksportować mapę, przesłać ją do innych osób, o ile posiada się Microsoft Outlook, albo zapisać jako swoje rozwiązanie, żeby można je było zaewidencjonować w kontroli wersji Team Foundation.

   ![Udostępnianie mapy kodu stosu wywołań innym osobom](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Jak mogę zatrzymać automatyczne dodawanie nowych stosów wywołań przez mapę?**

   Wybierz ![przycisk &#45; Pokaż stos wywołań na mapie kodu automatycznie](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") na pasku narzędzi Mapa. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij **klawisze CTRL**  +  **+ SHIFT**  +  **`** .

   Mapa nadal będzie wyróżniać istniejące stosy wywołań na mapie, którą debugujesz.

- **Co oznaczają ikony elementów i strzałki?**

   Aby uzyskać więcej informacji na temat elementu, przesuń wskaźnik myszy nad nim i poszukaj etykietki narzędzia elementu. Możesz również przyjrzeć się **legendzie** , aby dowiedzieć się, co oznacza każda ikona.

   ![Co oznaczają ikony na mapie kodu stosu wywołań?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Zobacz: [Mapowanie stosu wywołań](#MapStack) • [Tworzenie notatek dotyczących kodu](#MakeNotes) • [Aktualizacja mapy za pomocą następnego stosu wywołań](#UpdateMap) • [Dodawanie kodu pokrewnego do mapy](#AddRelatedCode) • [Znajdowanie błędów za pomocą mapy](#FindBugs)

## <a name="see-also"></a>Zobacz też
 [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) [używają map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md) [Znajdź potencjalne problemy przy użyciu analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md) [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md)
