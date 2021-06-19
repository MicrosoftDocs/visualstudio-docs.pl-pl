---
title: Metody mapowania dla stosu wywołań podczas debugowania
description: Dowiedz się, jak utworzyć mapę kodu w celu wizualnego śledzenia stosu wywołań podczas debugowania. Dowiedz się również, że możesz robić notatki na mapie, aby śledzić, co robi kod.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08fa0ff028140ebad421dd43fdfa53cc36b77804
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387492"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Metody mapowania dla stosu wywołań podczas debugowania w programie Visual Studio.

Utwórz mapę kodu, aby wizualnie śledzić stos wywołań podczas debugowania. Można robić notatki na mapie, żeby śledzić, jak zachowuje się kod, przez co można skoncentrować się na wyszukiwaniu błędów.

 ![Debugowanie za pomocą stosów wywołań na mapach kodu](../debugger/media/debuggermap_overview.png)

 Potrzebne będą następujące elementy:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range=">=vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Kod, który można debugować, taki jak Visual C#, Visual Basic, C++, JavaScript lub X++

  Zobacz:

- [Wideo: Debugowanie wizualne za pomocą integracji debugera mapy kodu (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Mapowanie stosu wywołań](#MapStack)

- [Notatki dotyczące kodu](#MakeNotes)

- [Aktualizowanie mapy przy użyciu następnego stosu wywołań](#UpdateMap)

- [Dodawanie powiązanego kodu do mapy](#AddRelatedCode)

- [Znajdowanie usterek przy użyciu mapy](#FindBugs)

- [Q & A](#QA)

  Aby uzyskać szczegółowe informacje o poleceniach i akcjach, których można użyć podczas pracy z mapami kodu, zobacz Przeglądanie i zmiana [układu map kodu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Mapowanie stosu wywołań

1. Uruchom debugowanie. (Klawiatura: **F5**)

2. Gdy aplikacja przejdzie w tryb przerwania lub przejdziesz do funkcji, wybierz pozycję **Mapa kodu**. (Klawiatura: **Ctrl**  +  **Shift**  +  **`** )

     ![Wybieranie mapy kodu w celu rozpoczęcia mapowania stosu wywołań](../debugger/media/debuggermap_choosecodemap.png)

     Bieżący stos wywołań jest wyświetlany w kolorze pomarańczowym na nowej mapie kodu:

     ![Wyświetlanie stosu wywołań na mapie kodu](../debugger/media/debuggermap_seeundocallstack.png)

     Mapa zostanie automatycznie zaktualizowana podczas kontynuowania debugowania. Zobacz [Aktualizowanie mapy przy użyciu następnego stosu wywołań](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Notatki dotyczące kodu

 Dodaj komentarze, aby śledzić, co dzieje się w kodzie. Aby dodać nowy wiersz w komentarzu, naciśnij **klawisze Shift + Return**.

 ![Dodawanie komentarza do stosu wywołań na mapie kodu](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Aktualizowanie mapy przy użyciu następnego stosu wywołań

 Uruchom aplikację do następnego punktu przerwania lub wejścia do funkcji. Mapa dodaje nowy stos wywołań.

 ![Aktualizowanie mapy kodu za pomocą następnego stosu wywołań](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Dodawanie powiązanego kodu do mapy

 Teraz masz mapę — co dalej? Jeśli pracujesz w języku C# lub Visual Basic, dodaj elementy, takie jak pola, właściwości i inne metody, aby śledzić, co dzieje się w kodzie.

 Kliknij dwukrotnie metodę, aby wyświetlić jej definicję kodu, lub użyj menu skrótów dla metody. (Klawiatura: wybierz metodę na mapie i naciśnij **klawisz F12)**

 ![Przejdź do definicji kodu dla metody na mapie kodu](../debugger/media/debuggermap_gotocodedefinition.png)

 Dodaj elementy, które chcesz śledzić na mapie.

 ![Pokazywanie pól w metodzie na mapie kodu stosu wywołań](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Domyślnie dodawanie elementów do mapy powoduje również dodanie węzłów grupy nadrzędnej, takich jak klasa, przestrzeń nazw i zestaw. Chociaż jest to przydatne, możesz zachować prostotę mapy,  wyłączając tę funkcję przy użyciu przycisku Uwzględnij elementy parents na pasku narzędzi mapy lub naciskając **klawisze CTRL** podczas dodawania elementów.

 ![Pola powiązane z metodą na mapie kodu stosu wywołań](../debugger/media/debuggermap_showedfields.png)

 W tym miejscu można łatwo zobaczyć, które metody wykorzystują te same pola. Ostatnio dodane elementy są wyświetlane w kolorze zielonym.

 Kontynuuj tworzenie mapy, aby zobaczyć więcej kodu.

 ![Zobacz metody, które używają pola: mapa kodu stosu wywołań](../debugger/media/debuggermap_findallreferences.png)

 ![Metody, które używają pola na mapie kodu stosu wywołań](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Znajdowanie usterek przy użyciu mapy

 Wizualizacja kodu pomoże w szybszym znalezieniu błędów. Załóżmy na przykład, że badasz usterkę w programie do rysowania. Po narysowaniu linii, w przypadku próby cofnięcia nic się nie dzieje, aż do rysowania kolejnej linii.

 Dlatego ustawiasz punkty przerwania w metodach , i , rozpocznij `clear` `undo` debugowanie i `Repaint` skompilowanie mapy podobnej do tej:

 ![Dodawanie kolejnego stosu wywołań do mapy kodu](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Zauważysz, że wszystkie gesty użytkownika w wywołaniu mapy `Repaint` , z wyjątkiem `undo` . Może to `undo` wyjaśnić, dlaczego nie działa natychmiast.

 Po naprawieniu usterki i kontynuowaniu działania programu mapa dodaje nowe wywołanie z do `undo` `Repaint` :

 ![Dodawanie nowego wywołania metody w celu wywołania stosu na mapie kodu](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Q & A

- **Nie wszystkie wywołania są wyświetlane na mapie. Dlaczego?**

   Domyślnie na mapie jest wyświetlany tylko Twój własny kod. Aby wyświetlić kod zewnętrzny, włącz go w **oknie Stos wywołań:**

   ![Wyświetlanie kodu zewnętrznego przy użyciu okna stosu wywołań](../debugger/media/debuggermap_callstackmenu.png)

   lub wyłącz **opcję Włącz Tylko mój kod** w opcjach Visual Studio debugowania:

   ![Wyświetlanie kodu zewnętrznego przy użyciu okna dialogowego Opcje](../debugger/media/debuggermap_debugoptions.png)

- **Czy zmiana mapy wpływa na kod?**

   Zmiana mapy w żaden sposób nie wpływa na kod. Możesz dowolnie zmienić nazwę, przenieść lub usunąć elementy na mapie.

- **Co oznacza ten komunikat: "Diagram może być oparty na starszej wersji kodu"?**

   Kod mógł ulec zmianie po ostatniej aktualizacji mapy. Na przykład wywołanie mapy może już nie istnieć w kodzie. Zamknij komunikat, a następnie spróbuj odbudować rozwiązanie przed ponowną aktualizacją mapy.

- **Jak mogę kontrolować układ mapy?**

   Otwórz menu **Układ** na pasku narzędzi mapy:

  - Zmiana układu domyślnego.

  - Aby automatycznie zatrzymać ponowne rozmieszczanie mapy, wyłącz pozycję **Układ automatyczny podczas debugowania.**

  - Aby jak najdrobniej zmienić rozmieszczenie mapy podczas dodawania elementów, wyłącz układ **przyrostowy**.

- **Czy mogę udostępnić mapę innym osobom?**

   Możesz wyeksportować mapę, wysłać ją do innych osób, jeśli masz program Microsoft Outlook, lub zapisać ją w rozwiązaniu, aby można było ją zaewidencjować w kontroli źródła.

   ![Udostępnianie innym osobom mapy kodu stosu wywołań](../debugger/media/debuggermap_sharewithothers.png)

- **Jak mogę mapie automatyczne dodawanie nowych stosów wywołań?**

   Wybierz ![ pozycję Przycisk&#45; automatycznie wyświetlaj stos wywołań na mapie ](../debugger/media/debuggermap_automaticupdateicon.gif) kodu na pasku narzędzi mapy. Aby ręcznie dodać bieżący stos wywołań do mapy, naciśnij **klawisze Ctrl**  +  **Shift**  +  **`** .

   Mapa będzie nadal wyróżniać istniejące stosy wywołań na mapie podczas debugowania.

- **Co oznaczają ikony i strzałki elementów?**

   Aby uzyskać więcej informacji na temat elementu, przesuń wskaźnik myszy na niego i spójrz na etykietkę narzędzia elementu. Możesz również przyjrzeć się **legendzie,** aby dowiedzieć się, co oznacza każda ikona.

   ![Co oznaczają ikony na mapie kodu stosu wywołań?](../debugger/media/debuggermap_showlegend.png)

  Zobacz:

- [Mapowanie stosu wywołań](#MapStack)

- [Notatki dotyczące kodu](#MakeNotes)

- [Aktualizowanie mapy przy użyciu następnego stosu wywołań](#UpdateMap)

- [Dodawanie powiązanego kodu do mapy](#AddRelatedCode)

- [Znajdowanie usterek przy użyciu mapy](#FindBugs)

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
