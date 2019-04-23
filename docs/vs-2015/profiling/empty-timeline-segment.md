---
title: Pusty Segment osi czasu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0291cfe93492c357401ce371d58683c6815aa12b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052821"
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Wizualizatorze współbieżności, przyczyna, dla której części osi czasu jest pusty (ma białe tło) jest zależna od typu kanału.  
  
- Dla kanału wątku procesora CPU oznacza to, że wątek nie istniał w tej części osi czasu. Jeśli interesuje Cię wątku, można znaleźć sekcji wykonywanie używający kontroli powiększenia lub przewijanie w poziomie.  
  
- W przypadku kanałem we/wy oznacza to, nie dostępu do dysku wystąpił w danym momencie imieniu procesu docelowego.  
  
- Dla kanału DirectX oznacza to, że nie działanie procesora GPU zostało wykonane imieniu procesu docelowego podczas tej części osi czasu.  
  
- Kanału znacznika oznacza to, czy nie wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Ustawianie powiększenia (Widok wątków)](../profiling/zoom-control-threads-view.md)
