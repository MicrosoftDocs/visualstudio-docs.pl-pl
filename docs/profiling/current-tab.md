---
title: Bieżąca karta | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48ba44d41286f1cf5eda6ececb68d21d39abd14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552791"
---
# <a name="current-tab"></a>Bieżąca karta
Klikając **bieżącą** kartę, można wyświetlić stos wywołań (jeśli jest dostępny), który znajduje się najbliżej bieżącego punktu wyboru na osi czasu, jeśli wybrano segment wątku procesora CPU.  W takim przypadku punkt wyboru jest reprezentowany przez czarną strzałkę lub cieszę nad osią czasu. Po wybraniu segmentu blokowania nie jest wyświetlany, ponieważ nie było wykonywania. Jednak segment jest nadal wyróżniony i wyświetlany jest stos wywołań.

 Na karcie **Bieżący** są również wyświetlane informacje o segmentach aktywności DirectX, znacznikach i dostępie we/wy.  W przypadku segmentów aktywności DirectX wyświetlane są informacje o sposobie przetwarzania pakietów DMA przez kolejkę sprzętową.  W przypadku znaczników wyświetlane są informacje o opisie i typie znacznika.  W przypadku dostępu we/wy wyświetlane są informacje o pliku i liczbie bajtów odczytanych lub zapisanych.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)