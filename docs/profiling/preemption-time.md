---
title: Czas wywłaszczania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935896"
---
# <a name="preemption-time"></a>Czas wywłaszczania
Te segmenty na osi czasu są skojarzone z czasu blokowania, które należą do kategorii wywłaszczania. Ta kategoria wynika, że wątek jest przełączenie ze względu na jeden z następujących powodów:

- Harmonogram zastąpiono ją za pomocą wyższy priorytet wątku.

- Wygasłe quantum wykonanie wątku, i inne wątki były gotowe do wykonania.

  W tym czasie wątek został zablokowany przez jądro powód oczekiwania, który zlicza Concurrency Visualizer jako wywłaszczania. Segmenty wywłaszczania Uruchom gdy wątek jest przekazywane poza rdzeń logiczny, a kończyć, kiedy wątek wznawia działanie.

  Etykietka narzędzia dla segmentu wyparte Wyświetla nazwę proces lub wątek, który spowodował wywłaszczania. Jednak to nie oznacza, że proces lub wątek, który zajął stanowisko dyrektora faktycznie uruchomiła przez cały okres preempted.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)