---
title: Pusty Segment osi czasu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3411de6fbc4d30f3b8dcb3dbe7a8eeba12e8ad9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959377"
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
W Wizualizatorze współbieżności, przyczyna, dla której części osi czasu jest pusty (ma białe tło) jest zależna od typu kanału.  
  
-   Dla kanału wątku procesora CPU oznacza to, że wątek nie istniał w tej części osi czasu. Jeśli interesuje Cię wątku, można znaleźć sekcji wykonywanie używający kontroli powiększenia lub przewijanie w poziomie.  
  
-   W przypadku kanałem we/wy oznacza to, nie dostępu do dysku wystąpił w danym momencie imieniu procesu docelowego.  
  
-   Dla kanału DirectX oznacza to, że nie działanie procesora GPU zostało wykonane imieniu procesu docelowego podczas tej części osi czasu.  
  
-   Kanału znacznika oznacza to, czy nie wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)