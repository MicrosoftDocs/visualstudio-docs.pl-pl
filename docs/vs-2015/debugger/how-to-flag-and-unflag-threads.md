---
title: 'Instrukcje: Oflagowanie i usuwanie oflagowania wątków | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be6ebe9e2031b24442f368b626d53b15a043023c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754149"
---
# <a name="how-to-flag-and-unflag-threads"></a>Instrukcje: Oflagowanie i usuwanie oflagowania wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można flagę wątku, który chcesz poświęcić szczególną uwagę, oznaczając je za pomocą ikony w **wątków**, **stosów równoległych**, **równoległego wyrażenia kontrolnego**, i **procesora GPU Wątki** systemu windows. Ta ikona może pomóc i inne odróżnić oflagowane wątki z innych wątków.  
  
 Oflagowane wątki otrzymają specjalnego traktowania w **wątku** listy na **Lokalizacja debugowania** paska narzędzi. Tej listy można wyświetlić wszystkie wątki lub tylko oflagowane wątki. Gdy Flagowanie wątku, **wątku** listy przełącza się do Pokaż tylko oflagowane wątki, ale można przełączyć go ponownie, aby wyświetlić wszystkie wątki, zgodnie z potrzebami.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Flaga lub usuń flagę wątku za pomocą okna wątków  
  
-   W **wątków** oknie Znajdź wątek Cię interesuje i kliknij ikonę flagi, aby zaznacz lub Wyczyść flagę.  
  
### <a name="to-unflag-all-threads"></a>Aby Usuń flagę ze wszystkich wątków  
  
-   W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie kliknij przycisk **Usuń flagę ze wszystkich wątków**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko oflagowane wątki  
  
-   Wybierz przycisk flagi w oknie debugowania.  
  
### <a name="to-flag-just-my-code"></a>Flagi tylko mój kod  
  
1.  Na pasku narzędzi u góry **wątków** okna, kliknij ikonę flagi.  
  
2.  Na liście rozwijanej kliknij **flagę tylko mój kod**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Aby Oflaguj wątki, które są skojarzone z wybranych modułów  
  
1.  Na pasku narzędzi **wątków** okna, kliknij ikonę flagi.  
  
2.  Na liście rozwijanej kliknij **Oflaguj niestandardowy wybór modułów**.  
  
3.  W **wybierz moduły** okna dialogowego Wybierz moduły, które chcesz.  
  
4.  (Opcjonalnie) W **wyszukiwania** wpisz ciąg do wyszukiwania określonych modułów.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Przewodnik: Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md)
