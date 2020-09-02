---
title: I-O Time (Widok wątków) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62995443"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako we/wy. Oznacza to, że wątek oczekuje na zakończenie operacji we/wy. Wątek mógł zostać zablokowany w interfejsie API lub przez jądro powiązane we/wy Zaczekaj, że Wizualizator współbieżności zlicza jako we/wy. Interfejsy API, takie jak `CreateFile()` , `ReadFile()` i `WSARecv()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)