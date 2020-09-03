---
title: Pusty segment osi czasu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179045"
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wizualizatorze współbieżności powód, dla którego sekcja osi czasu jest pusta (ma białe tło) zależy od rodzaju kanału.  
  
- W przypadku kanału wątku procesora CPU oznacza to, że wątek nie istniał w tej części osi czasu. Jeśli interesuje Cię wątek, możesz znaleźć jego sekcję wykonywania przy użyciu kontrolki powiększenia lub przewijania w poziomie.  
  
- W przypadku kanału we/wy oznacza to, że w tym momencie nie wystąpił dostęp do dysku w imieniu procesu docelowego.  
  
- W przypadku kanału DirectX oznacza to, że nie wykonano żadnych zadań procesora GPU w imieniu procesu docelowego w tej części osi czasu.  
  
- W przypadku kanału znacznika oznacza to, że nie Wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)
