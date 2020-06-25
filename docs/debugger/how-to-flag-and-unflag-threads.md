---
title: Jak flagować i rozflagować wątki | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7480f953e2fca57c296d6d1641059993bfa582c
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349630"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Instrukcje: Flagowanie i usuwanie flag wątków (C#, Visual Basic, C++)

Można oflagować wątek, który ma dawać szczególną uwagę, poprzez oznaczenie go ikoną w **wątkach**, **stosów równoległych** (Widok wątków), **zegarków równoległych**i **wątków GPU** . Ta ikona może pomóc Tobie i innym osobom odróżnić oflagowane wątki od innych wątków.

Wątki oflagowane otrzymują również specjalne traktowanie na liście **wątków** na pasku narzędzi **Lokalizacja debugowania** oraz w innych oknach debugowania wielowątkowego. Można pokazać wszystkie wątki lub tylko Oflagowane wątki na liście **wątków** lub w innych oknach.

### <a name="to-flag-or-unflag-a-thread"></a>Aby oflagować lub Usuń flagę wątku

- W oknie **wątki** lub **równoległe czujki** Znajdź interesujący Cię wątek i kliknij ikonę flagi, aby zaznaczyć lub wyczyścić flagę.
- W oknie **stosów równoległych** kliknij prawym przyciskiem myszy wątek lub grupę wątków i wybierz polecenie **Oflaguj/ \<thread> ** lub Usuń **flagę \<thread> / **.

### <a name="to-unflag-all-threads"></a>Aby Usuń flagę ze wszystkich wątków

- W oknie **wątki** kliknij prawym przyciskiem myszy dowolny wątek, a następnie kliknij pozycję Usuń **flagę wszystkie wątki**.
- W oknie **czujki równoległej** zaznacz wszystkie oflagowane wątki, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję Usuń **flagę**.

### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki

- Wybierz przycisk **Pokaż tylko Oflagowane wątki** w jednym z okien debugowania wielowątkowego.

### <a name="to-flag-just-my-code"></a>Aby oflagować Tylko mój kod

1. Na pasku narzędzi w górnej części okna **wątki** kliknij ikonę flagi.

2. Na liście rozwijanej kliknij pozycję **flaga tylko mój kod**.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Aby oflagować wątki, które są skojarzone z wybranymi modułami

1. Na pasku narzędzi okna **wątki** kliknij ikonę flagi.

2. Z listy rozwijanej kliknij pozycję **Oflaguj niestandardowy wybór modułu**.

3. W oknie dialogowym **Wybieranie modułów** wybierz odpowiednie moduły.

4. Obowiązkowe W polu **wyszukiwania** wpisz ciąg w celu wyszukania określonych modułów.

5. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Debuguj wielowątkowe aplikacje](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)
- [Przewodnik: debugowanie aplikacji wielowątkowych za pomocą okna wątków](../debugger/how-to-use-the-threads-window.md)