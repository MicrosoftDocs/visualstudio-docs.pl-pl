---
title: Czas synchronizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62965313"
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z czasami blokowania, które są klasyfikowane jako Synchronizacja. Gdy wątek jest oznaczony jako zablokowany podczas synchronizacji, jedna z następujących rzeczy jest implikowana:

- Wykonanie wątku mogło spowodować wywołanie dobrze znanego interfejsu API synchronizacji `EnterCriticalSection()` `WaitForSingleObject()`wątków, takiego jak lub .

- Algorytm dopasowywania interfejsu API nie może być całkowicie kompleksowy, dlatego niektóre interfejsy API, które mogą być mapowane na inne kategorie, mogą również być wyświetlane jako synchronizacja, ponieważ ramka w stosie wywołań ostatecznie osiągnęła podstawowy element blokady jądra, który był do tej kategorii.

  Aby zrozumieć przyczynę zdarzenia blokowania wątku, należy dokładnie zbadać stosy wywołań blokowania i raporty profilu.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)