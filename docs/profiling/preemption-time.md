---
title: Czas zastępujący | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935896"
---
# <a name="preemption-time"></a>Czas zastępujący
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako wywłaszczania. Ta kategoria oznacza, że wątek jest przełączany z jednego z następujących powodów:

- Harmonogram zamienił go przy użyciu wątku o wyższym priorytecie.

- Upłynął czas wykonywania wątku Quantum i inne wątki były gotowe do wykonania.

  W tym czasie wątek został zablokowany przez powód oczekiwania jądra, który jest używany przez Wizualizator współbieżności jako wywłaszczania. Segmenty przedwywłaszczania są uruchamiane, gdy wątek jest wypychany z rdzenia logicznego i kończy się, gdy ten wątek wznawia wykonywanie.

  Etykietka narzędzia dla segmentu przedwypartea wyświetla nazwę procesu lub wątku, który spowodował wystąpienie klasy pre-wywłaszczania. Nie oznacza to jednak, że proces lub wątek, który przeprzejął w rzeczywistości faktycznie działał w okresie przenoszonego.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)