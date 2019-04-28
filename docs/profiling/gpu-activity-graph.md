---
title: Wykres aktywności GPU | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969569"
---
# <a name="gpu-activity-graph"></a>Wykres aktywności procesora GPU
Wykres aktywności procesora GPU w Wizualizatorze współbieżności przedstawia poziomu aktywności DirectX w systemie, gdyż jest mierzone przez liczbę aparatów DirectX, które są używane wraz z upływem czasu.  Wykres nie pokazuje, które określonych aparatów były używane.  Aparat uznaje się będzie używana, jeśli przetwarza wszystkie działanie procesora GPU.

## <a name="gpu-activity-graph-colors"></a>Kolory wykres aktywności procesora GPU
 Zielony oznacza zużycia silników DirectX w bieżącym procesie.

 Jasny zwykle wskazuje zużycia silników DirectX przez inne procesy w systemie. Aby zmniejszyć zużycia silników DirectX przez inne procesy, Zmniejsz liczbę innych procesów uruchomionych w systemie.

 Oficjalny wskazuje dostępność nieużywane aparatów DirectX w systemie. Silników są dostępne dla procesu, jeśli możesz znaleźć dodatkowe możliwości w celu ich wykorzystania. Niektóre aparaty należy używać tylko dla określonych typów zadań.

## <a name="see-also"></a>Zobacz także
- [Widok wykorzystania](../profiling/utilization-view.md)