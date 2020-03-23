---
title: Wykres wykorzystania procesora | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552879"
---
# <a name="cpu-utilization-graph"></a>Wykres wykorzystania procesora
Wykres wykorzystania procesora CPU pokazuje poziom wykorzystania w aplikacji w czasie. Oś X reprezentuje czas trwania śledzenia, a oś y reprezentuje liczbę rdzeni logicznych w systemie. Wykres nie pokazuje, który określony rdzeń jest aktywny w danym momencie. Na przykład jeśli dwa rdzenie są uruchomione na 50 procent pojemności dla danego okresu czasu, a następnie ten widok pokazuje jeden rdzeń logiczny są wykorzystywane.

## <a name="cpu-utilization-graph-colors"></a>Kolory wykresu wykorzystania procesora

- Zielony wskazuje wykorzystanie rdzeni logicznych w systemie przez bieżący proces.

- Jasnoszary oznacza wykorzystanie rdzeni logicznych przez inne procesy w systemie. Wysoki procent jasnoszarego na wykresie procesora wskazuje, że system jest mocno obciążony przez inne procesy i że proces może być przez nich wyprzedzany. Aby zmniejszyć zużycie rdzeni logicznych przez inne procesy, zmniejsz ich liczbę w systemie.

- Ciemnoszary oznacza zużycie rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować tego, ale warto wiedzieć, kiedy występuje, ponieważ może to mieć wpływ na dostępność rdzeni logicznych dla procesu.

- Biały oznacza dostępność nieużywanych rdzeni logicznych w systemie. Rdzenie te są dostępne dla twojego procesu, jeśli można znaleźć więcej możliwości równoległości.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)
- [Średnie wykorzystanie procesora CPU](../profiling/average-cpu-utilization.md)