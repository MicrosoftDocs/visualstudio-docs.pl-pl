---
title: Wykres użycia procesora CPU | Microsoft Docs
description: Dowiedz się więcej na temat wykresu użycia procesora, który pokazuje poziom użycia w aplikacji z upływem czasu. Użycie jest wyświetlane jako liczba rdzeni logicznych używanych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5ec57ac6601557bf644c818822fea70a296fd0c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956012"
---
# <a name="cpu-utilization-graph"></a>Wykres użycia procesora CPU
Wykres użycia procesora CPU pokazuje poziom użycia w aplikacji z upływem czasu. Oś X reprezentuje czas trwania śledzenia, a oś y reprezentuje liczbę rdzeni logicznych w systemie. Wykres nie pokazuje, który konkretny rdzeń jest aktywny w danym momencie. Na przykład, jeśli dwa rdzenie są uruchamiane o 50 procent pojemności w danym okresie, ten widok pokazuje jeden rdzeń logiczny, który jest używany.

## <a name="cpu-utilization-graph-colors"></a>Kolory wykresu użycia procesora CPU

- Zielony wskazuje użycie rdzeni logicznych w systemie przez bieżący proces.

- Jasnoszary wskazuje wykorzystanie rdzeni logicznych przez inne procesy w systemie. Wysoka wartość procentowa szarego koloru na wykresie procesora CPU wskazuje, że system jest silnie załadowana przez inne procesy i że proces jest prawdopodobnie zastępujący. Aby zmniejszyć wykorzystanie rdzeni logicznych przez inne procesy, zmniejsz liczbę procesów uruchomionych w systemie.

- Ciemny szary wskazuje użycie rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować tego, ale warto wiedzieć, kiedy występuje, ponieważ może to mieć wpływ na dostępność rdzeni logicznych dla danego procesu.

- Kolor biały wskazuje dostępność nieużywanych rdzeni logicznych w systemie. Te rdzenie są dostępne dla procesu, jeśli można znaleźć więcej możliwości równoległości.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)
- [Średnie wykorzystanie CPU](../profiling/average-cpu-utilization.md)