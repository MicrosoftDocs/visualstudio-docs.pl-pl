---
title: Wykres wykorzystania procesora CPU | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e09526930bf98141ae4f9d4d204b20383763c208
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552879"
---
# <a name="cpu-utilization-graph"></a>Wykres wykorzystania procesora CPU
Wykres wykorzystania procesora CPU pokazuje poziom użycia w aplikacji wraz z upływem czasu. Oś x reprezentuje czas trwania śledzenia, a oś y — liczba rdzeni logicznych w systemie. Wykres nie pokazuje, w którym określonych podstawowe jest aktywny w dowolnym momencie. Na przykład jeśli każdy dwa rdzenie są uruchamiane o pojemności 50 procent w określonym czasie, ten widok przedstawia jednego rdzenia logicznego wykorzystywane.

## <a name="cpu-utilization-graph-colors"></a>Kolory Wykres wykorzystania procesora CPU

- Zielony oznacza użycie rdzeni logicznych w systemie przez bieżący proces.

- Jasny zwykle wskazuje użycie rdzeni logicznych przez inne procesy w systemie. Wysoki odsetek szarości światła w wykres czasu procesora CPU wskazuje, że system jest silnie obciążony przez inne procesy, i proces może być wyparte przez nich. Aby zmniejszyć zużycie rdzenie logiczne przez inne procesy, Zmniejsz liczbę ich działa w systemie.

- Ciemnoszary wskazuje użycia rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować to, ale warto wiedzieć, kiedy ma miejsce, ponieważ może mieć wpływ na dostępność rdzeni logicznych dla procesu.

- Oficjalny wskazuje dostępność nieużywane rdzenie logiczne w systemie. Rdzenie te są dostępne dla procesu, jeśli możesz znaleźć dodatkowe możliwości w równoległości obliczeń.

## <a name="see-also"></a>Zobacz także
- [Widok wykorzystania](../profiling/utilization-view.md)
- [Średnie wykorzystanie procesora CPU](../profiling/average-cpu-utilization.md)