---
title: Czas snu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62980216"
---
# <a name="sleep-time"></a>Czas snu
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest klasyfikowany jako uśpiony. Kategoria snu oznacza, że wątek dobrowolnie zrezygnował z logicznego rdzenia i nie wykonuje żadnej pracy. W tym czasie wątek został zablokowany w interfejsie API, który wizualizator współbieżności jest zliczanie jako uśpienia. Interfejsy API, `Sleep()` `SwitchToThread()` takie jak i należą do tej grupy.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)