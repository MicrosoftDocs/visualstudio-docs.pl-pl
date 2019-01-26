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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb4cf928426fb39adbbfdc18382b7d5de6c6b4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963687"
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