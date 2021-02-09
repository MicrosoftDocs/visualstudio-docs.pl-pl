---
title: Wykres aktywności procesora GPU | Microsoft Docs
description: Informacje na temat wykresu aktywności procesora GPU, który jest wyświetlany w wizualizatorze współbieżności w systemie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46f3e4ce7f155679bc3c701af90ff51e0fb20239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907281"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności procesora GPU
Wykres aktywności procesora GPU w programie Concurrency Visualizer wyświetla poziom aktywności DirectX w systemie mierzony przez liczbę aparatów DirectX, które są używane w miarę upływu czasu.  Wykres nie pokazuje, które konkretne aparaty zostały użyte.  Aparat jest uznawany za używany, jeśli przetwarza wszystkie działania procesora GPU.

## <a name="gpu-activity-graph-colors"></a>Kolory wykresu aktywności procesora GPU
 Zielony wskazuje użycie aparatów DirectX przez bieżący proces.

 Jasnoszary oznacza zużycie aparatów DirectX przez inne procesy w systemie. Aby zmniejszyć zużycie aparatów DirectX przez inne procesy, zmniejsz liczbę innych procesów uruchomionych w systemie.

 Kolor biały wskazuje dostępność nieużywanych aparatów DirectX w systemie. Te aparaty są dostępne dla procesu, jeśli znajdziesz więcej możliwości ich wykorzystania. Niektóre aparaty mogą być używane tylko dla określonych rodzajów zadań.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)