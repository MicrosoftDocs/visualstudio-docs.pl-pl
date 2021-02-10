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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6469c1020f125dd28798ad4bff5ccc9d3e7aa06
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949379"
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako synchronizacja. Gdy wątek zostanie oznaczony jako zablokowany podczas synchronizacji, jest to implikowana jedna z następujących sytuacji:

- Wykonanie wątku mogło spowodować wywołanie dobrze znanego interfejsu API synchronizacji wątku, takiego jak `EnterCriticalSection()` lub `WaitForSingleObject()` .

- Algorytm dopasowywania interfejsów API nie może być całkowicie kompleksowy, a w związku z tym niektóre interfejsy API, które mogą być mapowane na inne kategorie mogą być również wyświetlane jako synchronizacja, ponieważ ramka w stosie wywołań ostatecznie osiągnęła bazowe, blokowe elementy podstawowe, które zostały zmapowane do tej kategorii.

  Aby zrozumieć podstawową przyczynę zdarzenia blokowania wątku, należy uważnie sprawdzić stosy wywołań i raporty profilowe.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)