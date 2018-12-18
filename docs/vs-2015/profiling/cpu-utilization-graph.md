---
title: Wykres wykorzystania procesora CPU | Dokumentacja firmy Microsoft
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
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1eb8baeee066336834cc1fcfe427512108387a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726998"
---
# <a name="cpu-utilization-graph"></a>Wykres wykorzystania CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykres wykorzystania procesora CPU pokazuje poziom użycia w aplikacji wraz z upływem czasu. Oś x reprezentuje czas trwania śledzenia, a oś y — liczba rdzeni logicznych w systemie. Wykres nie pokazuje, w którym określonych podstawowe jest aktywny w dowolnym momencie. Na przykład jeśli każdy dwa rdzenie są uruchamiane o pojemności 50 procent w określonym czasie, ten widok przedstawia jednego rdzenia logicznego wykorzystywane.  
  
## <a name="cpu-utilization-graph-colors"></a>Kolory Wykres wykorzystania procesora CPU  
  
-   Zielony oznacza użycie rdzeni logicznych w systemie przez bieżący proces.  
  
-   Jasny zwykle wskazuje użycie rdzeni logicznych przez inne procesy w systemie. Wysoki odsetek szarości światła w wykres czasu procesora CPU wskazuje, że system jest silnie obciążony przez inne procesy, i proces może być wyparte przez nich. Aby zmniejszyć zużycie rdzenie logiczne przez inne procesy, Zmniejsz liczbę ich działa w systemie.  
  
-   Ciemnoszary wskazuje użycia rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować to, ale warto wiedzieć, kiedy ma miejsce, ponieważ może mieć wpływ na dostępność rdzeni logicznych dla procesu.  
  
-   Oficjalny wskazuje dostępność nieużywane rdzenie logiczne w systemie. Rdzenie te są dostępne dla procesu, jeśli możesz znaleźć dodatkowe możliwości w równoległości obliczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Średnie wykorzystanie procesora CPU](../profiling/average-cpu-utilization.md)



