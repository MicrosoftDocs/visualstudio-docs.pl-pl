---
title: Czas synchronizacji | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151382"
---
# <a name="synchronization-time"></a>Czas synchronizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako synchronizacja. Gdy wątek zostanie oznaczony jako zablokowany podczas synchronizacji, jest to implikowana jedna z następujących sytuacji:  
  
- Wykonanie wątku mogło spowodować wywołanie dobrze znanego interfejsu API synchronizacji wątku, takiego jak `EnterCriticalSection()` lub `WaitForSingleObject()` .  
  
- Algorytm dopasowywania interfejsów API nie może być całkowicie kompleksowy, a w związku z tym niektóre interfejsy API, które mogą być mapowane na inne kategorie mogą być również wyświetlane jako synchronizacja, ponieważ ramka w stosie wywołań ostatecznie osiągnęła bazowe, blokowe elementy podstawowe, które zostały zmapowane do tej kategorii.  
  
  Aby zrozumieć podstawową przyczynę zdarzenia blokowania wątku, należy uważnie sprawdzić stosy wywołań i raporty profilowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
