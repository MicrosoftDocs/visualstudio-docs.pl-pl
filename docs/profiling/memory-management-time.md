---
title: Czas zarządzania pamięcią | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62963784"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako zarządzanie pamięcią. Ten scenariusz oznacza, że wątek jest blokowany przez zdarzenie, które jest skojarzone z operacji zarządzania pamięcią, takich jak stronicowanie. W tym czasie wątek został zablokowany w stanie interfejsu API lub jądra, który wizualizator współbieżności jest zliczany jako zarządzanie pamięcią. Należą do nich zdarzenia, takie jak stronicowanie i alokacji pamięci.

 Sprawdź skojarzone stosy wywołań i raporty profilu, aby lepiej zrozumieć podstawowe przyczyny bloków, które są klasyfikowane jako zarządzanie pamięcią.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)