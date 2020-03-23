---
title: Wykres aktywności GPU | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5734b9eb1b4307f7c32dcb8a170f7c6c571f46ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969569"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności gpu
Wykres aktywności gpu w wizualizatorze współbieżności wyświetla poziom aktywności DirectX w systemie mierzony liczbą aparatów DirectX, które są używane w czasie.  Wykres nie pokazuje, które konkretne silniki zostały użyte.  Silnik jest uważany za używany, jeśli przetwarza pracę procesora gpu.

## <a name="gpu-activity-graph-colors"></a>Kolory wykresu aktywności gpu
 Zielony wskazuje zużycie silników DirectX przez bieżący proces.

 Jasnoszary oznacza zużycie silników DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie silników DirectX przez inne procesy, należy zmniejszyć liczbę innych procesów uruchomionych w systemie.

 Biały oznacza dostępność nieużywanych silników DirectX w systemie. Silniki te są dostępne dla twojego procesu, jeśli możesz znaleźć więcej możliwości ich wykorzystania. Niektóre aparaty mogą być używane tylko do określonych rodzajów zadań.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)