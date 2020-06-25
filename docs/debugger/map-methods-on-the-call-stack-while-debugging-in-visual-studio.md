---
title: Tworzenie mapy wizualnej stosu wywołań | Microsoft Docs
ms.date: 11/26/2018
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cf0cda942241ca77aa750624b6de25b5ae39391
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348538"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Tworzenie wizualnej mapy stosu wywołań podczas debugowania (C#, Visual Basic, C++, JavaScript)

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Możesz tworzyć notatki na mapie, aby śledzić, co robi kod, aby można było skupić się na znajdowaniu usterek.

Aby zapoznać się z przewodnikiem, Obejrzyj to wideo: [wideo: debugowanie wizualne za pomocą integracji z debugerem mapy kodu (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można używać z mapami kodu, zobacz [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Mapy kodu można tworzyć tylko w [wersji Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads).

Oto krótkie spojrzenie na mapę kodu:

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="map-the-call-stack"></a><a name="MapStack"></a>Mapowanie stosu wywołań

1. W Visual Studio Enterprise języku C#, Visual Basic, C++ lub JavaScript Rozpocznij debugowanie, wybierając **Debuguj**  >  **Rozpocznij debugowanie** lub naciskając klawisz **F5**.

1. Gdy aplikacja przejdzie w tryb przerwania lub przejdziesz do funkcji, wybierz pozycję **Debuguj**  >  **mapę kodu**lub naciśnij **klawisze CTRL** + **SHIFT** + **`** .

   Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

   ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Mapa kodu zostanie automatycznie zaktualizowana w miarę kontynuowania debugowania. Zmiana elementów mapy lub układu nie ma wpływu na kod. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

Aby uzyskać więcej informacji na temat elementu, umieść kursor nad nim i poszukaj etykietki narzędzia elementu. Możesz również wybrać **legendę** na pasku narzędzi, aby dowiedzieć się, co oznacza każda ikona.

![Legenda mapy kodu](../debugger/media/debuggermap_showlegend.png "Legenda mapy kodu")

>[!NOTE]
>Komunikat **, który diagram może opierać się na starszej wersji kodu** w górnej części mapy kodu, oznacza, że kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

## <a name="map-external-code"></a>Mapowanie kodu zewnętrznego

Domyślnie tylko własny kod jest wyświetlany na mapie. Aby wyświetlić kod zewnętrzny na mapie:

- Kliknij prawym przyciskiem myszy w oknie **stos wywołań** i wybierz polecenie **Pokaż kod zewnętrzny**:

  ![Wyświetlanie kodu zewnętrznego przy użyciu okna stosu wywołań](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Lub usuń zaznaczenie opcji **Włącz tylko mój kod** w **narzędziu** Visual Studio Tools (lub **Debug**) > **Options**  >  **debugowania**:

  ![Pokaż kod zewnętrzny przy użyciu okna dialogowego opcji](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Sterowanie układem mapy

Zmiana układu mapy nie ma wpływu na kod.

Aby kontrolować układ mapy, wybierz menu **Układ** na pasku narzędzi Mapa.

W menu **Układ** można:

- Zmiana układu domyślnego.
- Zatrzymaj automatyczną zmianę układu mapy, usuwając zaznaczenie opcji automatycznie rozmieszczaj **podczas debugowania**.
- Zmień rozmieszczenie mapy możliwie najbliżej podczas dodawania elementów, zaznaczając opcję **Układ przyrostowy**.

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a>Utwórz notatki dotyczące kodu

Możesz dodać komentarze, aby śledzić, co się dzieje w kodzie.

Aby dodać komentarz, kliknij prawym przyciskiem myszy na mapie kodu i wybierz polecenie **Edytuj**  >  **Nowy komentarz**, a następnie wpisz komentarz.

Aby dodać nowy wiersz w komentarzu, naciśnij klawisz **SHIFT** + **Enter**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>Aktualizowanie mapy za pomocą następnego stosu wywołań

Po uruchomieniu aplikacji do następnego punktu przerwania lub kroku do funkcji, Mapa automatycznie dodaje nowe stosy wywołań.

![Aktualizowanie mapy kodu przy użyciu następnego stosu wywołań](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Aby zatrzymać automatyczne dodawanie nowych stosów wywołań przez mapę, wybierz pozycję ![Pokaż stos wywołań na mapie kodu automatycznie](../debugger/media/debuggermap_automaticupdateicon.gif "Pokaż stos wywołań na mapie kodu automatycznie") na pasku narzędzi Mapa kodu. Mapa kontynuuje wyróżnianie istniejących stosów wywołań. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij **klawisze CTRL** + **+ SHIFT** + **`** .

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>Dodaj kod pokrewny do mapy

Teraz, gdy masz już mapę, w języku C# lub Visual Basic można dodawać elementy, takie jak pola, właściwości i inne metody, aby śledzić, co dzieje się w kodzie.

Aby przejść do definicji metody w kodzie, kliknij dwukrotnie metodę na mapie lub zaznacz ją i naciśnij klawisz **F12**lub kliknij ją prawym przyciskiem myszy i wybierz polecenie **Przejdź do definicji**.

![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Aby dodać elementy, które chcesz śledzić na mapie, kliknij prawym przyciskiem myszy metodę i wybierz elementy, które chcesz śledzić. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

![Pola związane z metodą na mapie kodu stosu wywołań](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Domyślnie Dodawanie elementów do mapy powoduje również dodanie węzłów grupy nadrzędnej, takich jak Klasa, przestrzeń nazw i zestaw. Tę funkcję można wyłączyć i włączyć, wybierając przycisk **Dołącz rodziców** na pasku narzędzi Mapa kodu lub naciskając klawisz **Ctrl** podczas dodawania elementów.

![Pokaż pola w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: Mapa kodu stosu wywołań](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody używające pola na mapie kodu stosu wywołań](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a>Znajdowanie usterek przy użyciu mapy
 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Załóżmy na przykład, że badasz usterkę w aplikacji do rysowania. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Dlatego należy ustawić punkty przerwania w `clear` `undo` metodach,, i `Repaint` , rozpocząć debugowanie i utworzyć mapę podobną do tej:

 ![Dodawanie kolejnego stosu wywołań do mapy kodu](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Zauważ, że wszystkie gesty użytkownika na mapie są wywoływane `Repaint` , z wyjątkiem `undo` . To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji uruchamiania aplikacji mapa dodaje nowe wywołanie z `undo` do `Repaint` :

 ![Dodaj nowe wywołanie metody do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Udostępnianie mapy innym osobom

Możesz wyeksportować mapę, wysłać ją do innych osób przy użyciu programu Microsoft Outlook, zapisać ją w rozwiązaniu i sprawdzić ją w kontroli wersji.

Aby udostępnić lub zapisać mapę, Użyj przycisk **Udostępnij** na pasku narzędzi mapy kodu.

![Udostępnianie mapy kodu stosu wywołań innym osobom](../debugger/media/debuggermap_sharewithothers.png "Udostępnianie mapy kodu stosu wywołań innym osobom")

## <a name="see-also"></a>Zobacz też
[Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

[Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
