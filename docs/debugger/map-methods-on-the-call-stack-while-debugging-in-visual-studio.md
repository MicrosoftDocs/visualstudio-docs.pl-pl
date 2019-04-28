---
title: Tworzenie wizualnej mapy stosu wywołań | Dokumentacja firmy Microsoft
ms.date: 11/26/2018
ms.topic: conceptual
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
ms.openlocfilehash: 3de5a3f9e9c5b8f89a9c8917794247098ba12d06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846805"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Tworzenie wizualnej mapy stosu wywołań podczas debugowania (C#, Visual Basic, C++, JavaScript)

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Możesz robić notatki na mapie, aby śledzić, co kod robi, dzięki czemu możesz skupić się na znajdowaniu usterek.

Aby uzyskać przewodnik Obejrzyj ten film wideo: [Wideo: Wizualne debugowanie dzięki integracji debugera mapy kodu (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Aby uzyskać szczegóły poleceń i akcji za pomocą map kodu, zobacz [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Można tworzyć tylko w mapy kodu [programu Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).

Poniżej przedstawiono krótkie omówienie mapy kodu:

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> Mapuj stos wywołań

1. W programie Visual Studio Enterprise C#, Visual Basic, C++ lub JavaScript projektu, Rozpocznij debugowanie wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając **F5**.

1. Po skopiowaniu aplikacja przejdzie do trybu podziału lub wkroczysz do funkcji, wybierz **debugowania** > **mapy kodu**, lub naciśnij **Ctrl**+**Shift** +**`**.

   Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

   ![Zobacz stos wywołań na mapie kodu](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Kod automatycznego mapowania aktualizacji możesz kontynuować debugowanie. Zmiana elementów mapy lub układu nie ma wpływu na kod w dowolny sposób. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

Aby uzyskać więcej informacji na temat elementu, umieść kursor nad nią i przyjrzyj się etykietka narzędzia elementu. Możesz również wybrać **legendy** na pasku narzędzi, aby dowiedzieć się, co oznacza każda ikona.

![Kod legendę mapy](../debugger/media/debuggermap_showlegend.png "legendę mapy kodu")

>[!NOTE]
>Komunikat **diagramu mogą opierać na starszej wersji kodu** w górnej części kodu mapy oznacza, że kod mogły ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

## <a name="map-external-code"></a>Mapy kodu zewnętrznego

Domyślnie tylko Twój własny kod pojawia się na mapie. Aby wyświetlić kod zewnętrzny na mapie:

- Kliknij prawym przyciskiem myszy **stos wywołań** okna, a następnie wybierz pozycję **Pokaż kod zewnętrzny**:

  ![Wyświetlić kod zewnętrzny, w oknie stosu wywołań](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Lub Anuluj wybór **Włącz tylko mój kod** w programie Visual Studio **narzędzia** (lub **debugowania**) > **opcje**  >   **Debugowanie**:

  ![Pokaż kod zewnętrzny, za pomocą okna dialogowego Opcje](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Kontrolować układ mapy

Zmienianie układu mapy nie ma wpływu na kod w dowolny sposób.

Aby kontrolować układ mapy, wybierz **układ** menu na pasku narzędzi mapy.

W **układ** menu, możesz:

- Zmiana układu domyślnego.
- Zatrzymać automatyczne rozmieszczanie na mapie, anulując **automatycznie rozmieszczaj podczas debugowania**.
- Ponowne rozmieszczanie map jak najmniejszy podczas dodawania elementów, nie zaznaczaj opcji **układ Przyrostowy**.

## <a name="MakeNotes"></a> Robienie notatek dotyczących kodu

Można dodawać komentarze, aby śledzić, co się dzieje w kodzie.

Aby dodać komentarz, kliknij prawym przyciskiem myszy na mapie kodu, a następnie wybierz **Edytuj** > **nowy komentarz**, następnie wpisz komentarz.

Aby dodać nowy wiersz w komentarzu, naciśnij **Shift**+**Enter**.

 ![Dodaj komentarz do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aktualizacja mapy za pomocą następnego stosu wywołań

Podczas uruchamiania aplikacji do następnego punktu przerwania lub wejścia do funkcji mapy automatycznie dodaje nowych stosów wywołań.

![Aktualizacja mapy kodu za pomocą następnego stosu wywołań](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Aby zatrzymać automatyczne dodawanie nowych stosów wywołań do mapy, wybierz ![Pokaż automatycznie umieszczane na mapie kodu](../debugger/media/debuggermap_automaticupdateicon.gif "Pokaż automatycznie umieszczane na mapie kodu") na pasku narzędzi mapy kodu. Mapa nadal wyróżniać istniejące stosy wywołań. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij klawisz **Ctrl**+**Shift**+**`**.

## <a name="AddRelatedCode"></a> Dodawanie kodu pokrewnego do mapy

Teraz, gdy masz mapę, w C# lub Visual Basic, możesz dodać elementy, takie jak pola, właściwości i innych metod, aby śledzić, co się dzieje w kodzie.

Aby przejść do definicji metody w kodzie, kliknij dwukrotnie metodę na mapie lub wybierz ją i naciśnij klawisz **F12**, lub kliknij ją prawym przyciskiem myszy i wybierz polecenie **przejdź do definicji**.

![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Aby dodać elementy, które chcesz śledzić na mapie, kliknij prawym przyciskiem myszy metodę, a następnie wybierz elementy, które mają być śledzone. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

![Pola powiązane z metodę na mapie kodu stosu wywołań](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Domyślnie Dodawanie elementów do mapy dodaje również węzły nadrzędne grupy, takie jak klasy, przestrzeni nazw i zestawu. Można włączyć tę funkcję i wyłączonym, wybierając **obejmują elementy nadrzędne** przycisk na pasku narzędzi Mapa kodu lub naciskając **Ctrl** podczas dodawania elementów.

![Pokazywanie pól w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: mapy kodu w stosie wywołań](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody używające pole na mapie kodu stosu wywołań](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Znajdowanie błędów za pomocą mapy
 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Na przykład załóżmy, że analizujesz błąd w aplikacji rysowania. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Aby ustawić punkty przerwania `clear`, `undo`, i `Repaint` metod, rozpocząć debugowanie i utworzyć mapę podobną do tego:

 ![Dodaj inny stos wywołań do mapy kodu](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Należy zauważyć, że wszystkie gesty użytkownika na mapie wywołują `Repaint`, z wyjątkiem `undo`. To może wyjaśnić, dlaczego `undo` nie działa natychmiast.

 Po naprawieniu błędu i kontynuacji działania aplikacji, mapa dodaje nowe wywołanie z `undo` do `Repaint`:

 ![Dodaj nowy stos wywołań do wywołania metody na mapie kodu](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Dzielić się mapami z innymi użytkownikami

Można eksportować mapę, wysłać ją do innych osób z programem Microsoft Outlook, zapisz go do rozwiązania i sprawdź go do kontroli wersji.

Aby udostępnić lub zapisać mapy, należy użyć **udostępnianie** na pasku narzędzi mapy kodu.

![Mapy kodu stosu wywołań udostępniania innym osobom](../debugger/media/debuggermap_sharewithothers.png "mapy kodu stosu wywołań udostępniania innym osobom")

## <a name="see-also"></a>Zobacz także
[Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

[Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
