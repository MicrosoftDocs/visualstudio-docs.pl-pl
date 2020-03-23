---
title: Czas we/wy (widok wątków) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62995443"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako operacje we/wy. Oznacza to, że wątek oczekuje na zakończenie operacji we/wy. Wątek mógł zostać zablokowany w interfejsie API lub przez jądro związane z we/wy czekać, że wizualizator współbieżności jest liczony jako we/wy. Interfejsy API, `CreateFile()` `ReadFile()`takie `WSARecv()` jak , i należą do tej grupy.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)