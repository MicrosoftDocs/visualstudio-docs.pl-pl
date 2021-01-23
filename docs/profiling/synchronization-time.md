---
title: Czas synchronizacji | Microsoft Docs
description: Dowiedz się, jak segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako synchronizacja.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0e8c2243d01a5801b6846445995bbdfdcff78c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719828"
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako synchronizacja. Gdy wątek zostanie oznaczony jako zablokowany podczas synchronizacji, jest to implikowana jedna z następujących sytuacji:

- Wykonanie wątku mogło spowodować wywołanie dobrze znanego interfejsu API synchronizacji wątku, takiego jak `EnterCriticalSection()` lub `WaitForSingleObject()` .

- Algorytm dopasowywania interfejsów API nie może być całkowicie kompleksowy, a w związku z tym niektóre interfejsy API, które mogą być mapowane na inne kategorie mogą być również wyświetlane jako synchronizacja, ponieważ ramka w stosie wywołań ostatecznie osiągnęła bazowe, blokowe elementy podstawowe, które zostały zmapowane do tej kategorii.

  Aby zrozumieć podstawową przyczynę zdarzenia blokowania wątku, należy uważnie sprawdzić stosy wywołań i raporty profilowe.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)