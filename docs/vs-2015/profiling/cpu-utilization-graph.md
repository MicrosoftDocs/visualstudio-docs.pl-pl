---
title: Wykres użycia procesora CPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8058995c8ae45c40f202aaa1e788891da3eb985d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180489"
---
# <a name="cpu-utilization-graph"></a>Wykres wykorzystania CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykres użycia procesora CPU pokazuje poziom użycia w aplikacji z upływem czasu. Oś X reprezentuje czas trwania śledzenia, a oś y reprezentuje liczbę rdzeni logicznych w systemie. Wykres nie pokazuje, który konkretny rdzeń jest aktywny w danym momencie. Na przykład, jeśli dwa rdzenie są uruchamiane o 50 procent pojemności w danym okresie, ten widok pokazuje jeden rdzeń logiczny, który jest używany.  
  
## <a name="cpu-utilization-graph-colors"></a>Kolory wykresu użycia procesora CPU  
  
- Zielony wskazuje użycie rdzeni logicznych w systemie przez bieżący proces.  
  
- Jasnoszary wskazuje wykorzystanie rdzeni logicznych przez inne procesy w systemie. Wysoka wartość procentowa jasnego szarego wykresu CPU wskazuje, że system jest silnie załadowana przez inne procesy i że proces jest prawdopodobnie wyparte przez nie. Aby zmniejszyć wykorzystanie rdzeni logicznych przez inne procesy, zmniejsz liczbę procesów uruchomionych w systemie.  
  
- Ciemny szary wskazuje użycie rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować tego, ale warto wiedzieć, kiedy występuje, ponieważ może to mieć wpływ na dostępność rdzeni logicznych dla danego procesu.  
  
- Kolor biały wskazuje dostępność nieużywanych rdzeni logicznych w systemie. Te rdzenie są dostępne dla procesu, jeśli można znaleźć więcej możliwości równoległości.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Średnie wykorzystanie CPU](../profiling/average-cpu-utilization.md)
