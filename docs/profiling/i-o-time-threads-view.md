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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915ab6aef595fba7e13321d4e23c08bdd2eadaf3
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721635"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako we/wy. Oznacza to, że wątek oczekuje na zakończenie operacji we/wy. Wątek mógł zostać zablokowany w interfejsie API lub przez jądro powiązane we/wy Zaczekaj, że Wizualizator współbieżności zlicza jako we/wy. Interfejsy API, takie jak `CreateFile()` , `ReadFile()` i `WSARecv()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)