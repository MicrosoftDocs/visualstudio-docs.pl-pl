---
title: Czas zarządzania pamięcią | Microsoft Docs
description: Zapoznaj się z tym scenariuszem, że wątek jest blokowany przez zdarzenie skojarzone z operacją zarządzania pamięcią, taką jak stronicowanie.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e1dd2868f5b29a12f3f54f46e5cb5833d270af
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721206"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako zarządzanie pamięcią. Ten scenariusz oznacza, że wątek jest blokowany przez zdarzenie skojarzone z operacją zarządzania pamięcią, taką jak stronicowanie. W tym czasie wątek został zablokowany w interfejsie API lub jądra, który jest obliczany przez Wizualizator współbieżności jako zarządzanie pamięcią. Obejmują one zdarzenia, takie jak stronicowanie i alokacja pamięci.

 Przejrzyj skojarzone stosy wywołań i raporty profilowe, aby lepiej zrozumieć podstawowe przyczyny dotyczące bloków, które są klasyfikowane jako zarządzanie pamięcią.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)