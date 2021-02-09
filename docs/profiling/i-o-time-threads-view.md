---
title: I-O Time (Widok wątków) | Microsoft Docs
description: Dowiedz się, jak segmenty czasu we/wy są skojarzone z czasem blokowania, które są klasyfikowane jako operacje we/wy, co oznacza, że wątek oczekuje na zakończenie operacji we/wy.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906862"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako we/wy. Oznacza to, że wątek oczekuje na zakończenie operacji we/wy. Wątek mógł zostać zablokowany w interfejsie API lub przez jądro powiązane we/wy Zaczekaj, że Wizualizator współbieżności zlicza jako we/wy. Interfejsy API, takie jak `CreateFile()` , `ReadFile()` i `WSARecv()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)