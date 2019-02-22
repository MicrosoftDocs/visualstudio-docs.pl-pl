---
title: -O Time (Widok wątków) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625455"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z zablokowania prób są podzielone na We/Wy. Oznacza to, że wątek czeka na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub zaczekaj I dotyczących wejścia/wyjścia jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takie jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)