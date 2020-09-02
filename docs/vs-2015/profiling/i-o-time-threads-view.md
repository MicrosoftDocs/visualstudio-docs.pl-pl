---
title: I-O Time (Widok wątków) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86c14292edcf8f132a14b67e931c5121105a9dc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187445"
---
# <a name="io-time-threads-view"></a>I/O Time (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako we/wy. Oznacza to, że wątek oczekuje na zakończenie operacji we/wy. Wątek mógł zostać zablokowany w interfejsie API lub przez jądro powiązane we/wy Zaczekaj, że Wizualizator współbieżności zlicza jako we/wy. Interfejsy API, takie jak `CreateFile()` , `ReadFile()` i `WSARecv()` mieszczą się w tej grupie.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
