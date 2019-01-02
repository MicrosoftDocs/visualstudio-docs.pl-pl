---
title: Czas uśpienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53f9137c35bd89e812f1d671e2e51f88b343753c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920261"
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z czasu blokowania, które należą do kategorii uśpienia. Kategoria uśpienia oznacza, że wątek dobrowolnie dało się jego rdzeń logiczny i wykonując żadnej pracy. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako uśpienia. Interfejsy API, takie jak `Sleep()` i `SwitchToThread()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)