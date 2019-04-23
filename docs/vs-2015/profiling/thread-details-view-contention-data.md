---
title: Widok szczegółów wątku - dane Kontencji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16ee86e69cb3a150a98de5077aa0c545545833e8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069110"
---
# <a name="thread-details-view---contention-data"></a>Widok szczegółów wątku — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok szczegółów wątku przedstawia wykres osi czasu blokowania zdarzeń w wybranym wątku przebiegu profilowania, które były spowodowane przez rywalizacji nad zasobami. Blokowanie zdarzenie występuje, gdy wątek jest zmuszony do zawieszenia wykonania, ponieważ inny wątek został zablokowany dostęp do zasobu.  
  
 Ten widok przedstawia oś czasu wykonywania zdarzeń blokujących jako pionowy pasek na osi poziomej dla wątku i wątku, jako poziomy pasek. Gdy jest to konieczne, można powiększyć części osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżki wykonywania funkcji, które doprowadziły do zdarzenia, kliknij pasek zdarzeń. Funkcje są wyświetlane w oknie stosu wywołań. Jeśli kod źródłowy dla funkcji jest dostępny, możesz kliknąć nazwę funkcji, aby edytować plik źródłowy w środowisku IDE programu Visual Studio.  
  
## <a name="navigating-the-timeline"></a>Przejdź na osi czasu  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Aby powiększyć segment osi czasu  
  
- Kliknij i przeciągnij wskaźnik myszy, aby wybrać obszar osi czasu.  
  
     Po zwolnieniu przycisku myszy widok powiększa do segmentu wybrana wartość czasu. Możesz powtórzyć proces powiększenia bardziej szczegółowo. Pole przewijania na pasku przewijania czas reprezentuje rozmiar względny, segmentu czas, który jest wyświetlany w widoku.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu  
  
- Kliknij przycisk **Pomniejsz** aby powrócić do poprzedniego poziomu powiększenia.  
  
- Kliknij przycisk **resetowania powiększenia** do wyświetlenia całego osi czasu w widoku.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzenia  
  
- W wykres osi czasu kliknij pasek pionowy, który reprezentuje zdarzenie...  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kod źródłowy funkcji w stosie wywołań  
  
- W oknie wywołania stosu kliknij nazwę funkcji.  
  
  Kod źródłowy funkcji musi być częścią bieżącego projektu.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Aby wyświetlić wszystkie wątki podczas uruchomienia profilowania zdarzenia rywalizacji o zasób  
  
- Na wykresie osi czasu kliknij nazwę lub identyfikator zasobu.  
  
     [Widok szczegółów zasobów](../profiling/resource-details-view-contention-data.md) pojawia się dla wybranego zasobu.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Aby wyświetlić dane rywalizacji wątków w okno procesów  
  
- Wykres osi czasu, kliknij **całkowita**.  
  
     [Widok procesu](../profiling/process-view-contention-data.md) pojawia się za pomocą wątku wybrane.
