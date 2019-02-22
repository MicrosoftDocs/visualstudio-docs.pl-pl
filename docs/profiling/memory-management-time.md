---
title: Czas zarządzania pamięcią | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 442973edb18e75bafda8a9397eac799286c69dfa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609374"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
Te segmenty na osi czasu są skojarzone z zablokowania prób są podzielone na zarządzanie pamięcią. Ten scenariusz oznacza, że wątek jest zablokowany przez zdarzenie, który jest skojarzony z operacji zarządzania pamięcią, takich jak stronicowania. W tym czasie wątek został zablokowany w stanie interfejsu API lub jądra Concurrency Visualizer jest liczy się jako zarządzania pamięcią. Obejmują one zdarzenia, takie jak Alokacja pamięci i stronicowania.

 Sprawdź stosy wywołań skojarzone i profilu, aby lepiej zrozumieć podstawowe przyczyny bloki, które są podzielone na zarządzanie pamięcią raportów.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)