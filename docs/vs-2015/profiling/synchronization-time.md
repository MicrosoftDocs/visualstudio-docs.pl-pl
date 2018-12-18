---
title: Czas synchronizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76775ca0270b46c17506106640ba2d68e795049b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755386"
---
# <a name="synchronization-time"></a>Czas synchronizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako synchronizacji. Gdy wątek jest oznaczony jako zablokowane na synchronizacji, jeden z nich jest implikowane:  
  
- Wykonywanie wątku może spowodować utworzenie wywołanie synchronizacji wątków dobrze znanych interfejsów API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
- Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektóre interfejsy API, który mógłby być mapowany na innych kategoriach może również wystąpić, ponieważ synchronizacji, ponieważ ramki w wywołaniu stosu po pewnym czasie osiągnięto bazowego jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
  Aby zrozumieć przyczyny wydarzeniu blokowania wątku, należy dokładnie bada blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



