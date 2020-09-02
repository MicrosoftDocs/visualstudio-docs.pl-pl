---
title: Czas synchronizacji | Microsoft Docs
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
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62965313"
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako synchronizacja. Gdy wątek zostanie oznaczony jako zablokowany podczas synchronizacji, jest to implikowana jedna z następujących sytuacji:

- Wykonanie wątku mogło spowodować wywołanie dobrze znanego interfejsu API synchronizacji wątku, takiego jak `EnterCriticalSection()` lub `WaitForSingleObject()` .

- Algorytm dopasowywania interfejsów API nie może być całkowicie kompleksowy, a w związku z tym niektóre interfejsy API, które mogą być mapowane na inne kategorie mogą być również wyświetlane jako synchronizacja, ponieważ ramka w stosie wywołań ostatecznie osiągnęła bazowe, blokowe elementy podstawowe, które zostały zmapowane do tej kategorii.

  Aby zrozumieć podstawową przyczynę zdarzenia blokowania wątku, należy uważnie sprawdzić stosy wywołań i raporty profilowe.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)