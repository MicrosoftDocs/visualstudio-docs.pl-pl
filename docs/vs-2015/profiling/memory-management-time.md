---
title: Czas zarządzania pamięcią | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3fc38abb47c70949b63b44958e96e3b168589fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729418"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z zablokowania prób są podzielone na zarządzanie pamięcią. Oznacza to, że wątek jest zablokowany przez zdarzenie, który jest skojarzony z operacji zarządzania pamięcią, takich jak stronicowania. W tym czasie wątek został zablokowany w stanie interfejsu API lub jądra Concurrency Visualizer jest liczy się jako zarządzania pamięcią. Obejmują one zdarzenia, takie jak Alokacja pamięci i stronicowania.  
  
 Sprawdź stosy wywołań skojarzone i profilu, aby lepiej zrozumieć podstawowe przyczyny bloki, które są podzielone na zarządzanie pamięcią raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



