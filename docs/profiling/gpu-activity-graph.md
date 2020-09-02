---
title: Wykres aktywności procesora GPU | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969569"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności procesora GPU
Wykres aktywności procesora GPU w programie Concurrency Visualizer wyświetla poziom aktywności DirectX w systemie mierzony przez liczbę aparatów DirectX, które są używane w miarę upływu czasu.  Wykres nie pokazuje, które konkretne aparaty zostały użyte.  Aparat jest uznawany za używany, jeśli przetwarza wszystkie działania procesora GPU.

## <a name="gpu-activity-graph-colors"></a>Kolory wykresu aktywności procesora GPU
 Zielony wskazuje użycie aparatów DirectX przez bieżący proces.

 Jasnoszary oznacza zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, zmniejsz liczbę innych procesów uruchomionych w systemie.

 Kolor biały wskazuje dostępność nieużywanych aparatów DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli znajdziesz więcej możliwości ich wykorzystania. Niektóre aparaty mogą być używane tylko dla określonych rodzajów zadań.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)