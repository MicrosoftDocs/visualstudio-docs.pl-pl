---
title: Czas synchronizacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151382"
---
# <a name="synchronization-time"></a>Czas synchronizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako synchronizacji. Gdy wątek jest oznaczony jako zablokowane na synchronizacji, jeden z nich jest implikowane:  
  
- Wykonywanie wątku może spowodować utworzenie wywołanie synchronizacji wątków dobrze znanych interfejsów API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
- Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektóre interfejsy API, który mógłby być mapowany na innych kategoriach może również wystąpić, ponieważ synchronizacji, ponieważ ramki w wywołaniu stosu po pewnym czasie osiągnięto bazowego jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
  Aby zrozumieć przyczyny wydarzeniu blokowania wątku, należy dokładnie bada blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
