---
title: 'Instrukcje: Flagowanie i usuwanie flag wątków | Microsoft Docs'
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
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189442"
---
# <a name="how-to-flag-and-unflag-threads"></a>Porada: Oflagowanie i usuwanie oflagowania wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można oflagować wątek, który ma dawać szczególną uwagę, poprzez oznaczenie go ikoną w **wątkach**, **stosów równoległych**, **zegarków równoległych**i **wątków GPU** . Ta ikona może pomóc Tobie i innym osobom odróżnić oflagowane wątki od innych wątków.  
  
 Wątki oflagowane otrzymują również specjalne traktowanie na liście **wątków** na pasku narzędzi **Lokalizacja debugowania** . Ta lista może zawierać wszystkie wątki lub tylko Oflagowane wątki. Po oznaczeniu wątku na liście **wątków** automatycznie przełączane są tylko Oflagowane wątki, ale można je przełączyć z powrotem, aby pokazać wszystkie wątki zgodnie z potrzebami.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Aby oflagować wątek lub usuń jego flagę przy użyciu okna wątków  
  
- W oknie **wątki** Znajdź interesujący Cię wątek i kliknij ikonę flagi, aby zaznaczyć lub wyczyścić flagę.  
  
### <a name="to-unflag-all-threads"></a>Aby Usuń flagę ze wszystkich wątków  
  
- W oknie **wątki** kliknij prawym przyciskiem myszy dowolny wątek, a następnie kliknij pozycję Usuń **flagę wszystkie wątki**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki  
  
- Wybierz przycisk flagi w oknie Debugowanie.  
  
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
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Przewodnik: debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md)
