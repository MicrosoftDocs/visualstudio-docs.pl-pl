---
title: Czas zarządzania pamięcią | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48cbdd523f4527af84c52366a439a18330e1828c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157345"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako zarządzanie pamięcią. Oznacza to, że wątek jest blokowany przez zdarzenie skojarzone z operacją zarządzania pamięcią, taką jak stronicowanie. W tym czasie wątek został zablokowany w interfejsie API lub jądra, który jest obliczany przez Wizualizator współbieżności jako zarządzanie pamięcią. Obejmują one zdarzenia, takie jak stronicowanie i alokacja pamięci.  
  
 Przejrzyj skojarzone stosy wywołań i raporty profilowe, aby lepiej zrozumieć podstawowe przyczyny dotyczące bloków, które są klasyfikowane jako zarządzanie pamięcią.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
