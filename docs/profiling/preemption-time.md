---
title: Czas wywłaszczenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62935896"
---
# <a name="preemption-time"></a>Czas wywłaszczenia
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest klasyfikowany jako Pierwok. Ta kategoria oznacza, że wątek jest wyłączony z jednego z następujących powodów:

- Harmonogram zastąpił go przy użyciu wątku o wyższym priorytecie.

- Kwantowa wykonanie wątku wygasła i inne wątki były gotowe do wykonania.

  W tym czasie wątek został zablokowany przez jądro czekać powodu, że wizualizator współbieżności jest zliczanie jako pre-emption. Segmenty pierkupu rozpoczynają się, gdy wątek jest wypychany z rdzenia logicznego i kończą się, gdy ten wątek wznawia wykonywanie.

  Etykietka narzędzia dla segmentu wywłaszczonego wyświetla nazwę procesu lub wątku, który spowodował wywłaszczanie. Nie oznacza to jednak, że proces lub wątek, który przejął faktycznie prowadził przez cały wywłaszczony okres.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)