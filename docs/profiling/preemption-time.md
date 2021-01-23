---
title: Czas zastępujący | Microsoft Docs
description: Dowiedz się więcej na temat czasu Premption i tego, że segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako pre-wywłaszczania.
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
ms.openlocfilehash: a102b11fdc7608b94b97105b061e28860f41a9a1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719516"
---
# <a name="preemption-time"></a>Czas zastępujący
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako wywłaszczania. Ta kategoria oznacza, że wątek jest przełączany z jednego z następujących powodów:

- Harmonogram zamienił go przy użyciu wątku o wyższym priorytecie.

- Upłynął czas wykonywania wątku Quantum i inne wątki były gotowe do wykonania.

  W tym czasie wątek został zablokowany przez powód oczekiwania jądra, który jest używany przez Wizualizator współbieżności jako wywłaszczania. Segmenty przedwywłaszczania są uruchamiane, gdy wątek jest wypychany z rdzenia logicznego i kończy się, gdy ten wątek wznawia wykonywanie.

  Etykietka narzędzia dla segmentu przedwypartea wyświetla nazwę procesu lub wątku, który spowodował wystąpienie klasy pre-wywłaszczania. Nie oznacza to jednak, że proces lub wątek, który przeprzejął w rzeczywistości faktycznie działał w okresie przenoszonego.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)