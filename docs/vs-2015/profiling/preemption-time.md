---
title: Czas zastępujący | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198063"
---
# <a name="preemption-time"></a>Czas wywłaszczania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako zastępujący. Ta kategoria oznacza, że wątek jest przełączany z jednego z następujących powodów:  
  
- Harmonogram zamienił go przy użyciu wątku o wyższym priorytecie.  
  
- Upłynął czas wykonywania wątku Quantum i inne wątki były gotowe do wykonania.  
  
  W tym czasie wątek został zablokowany przez powód oczekiwania jądra, który jest używany przez Wizualizator współbieżności jako zastępujący. Segmenty przeprowadzenia zastępują uruchomione, gdy wątek zostanie wysunięty z rdzenia logicznego i kończyć się, gdy ten wątek wznowi wykonywanie.  
  
  Etykietka narzędzia dla segmentu przeniesiona zawiera nazwę procesu lub wątku, który spowodował zastępujący. Nie oznacza to jednak, że proces lub wątek, który przeprzejął w rzeczywistości faktycznie działał w okresie przenoszonego.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
