---
title: Wykres aktywności procesora GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434220"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykres aktywności procesora GPU w programie Concurrency Visualizer wyświetla poziom aktywności DirectX w systemie mierzony przez liczbę aparatów DirectX, które są używane w miarę upływu czasu.  Wykres nie pokazuje, które konkretne aparaty zostały użyte.  Aparat jest uznawany za używany, jeśli przetwarza wszystkie działania procesora GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Kolory wykresu aktywności procesora GPU  
 Zielony wskazuje użycie aparatów DirectX przez bieżący proces.  
  
 Jasnoszary oznacza zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, zmniejsz liczbę innych procesów uruchomionych w systemie.  
  
 Kolor biały wskazuje dostępność nieużywanych aparatów DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli znajdziesz więcej możliwości ich wykorzystania. Niektóre aparaty mogą być używane tylko dla określonych rodzajów zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)
