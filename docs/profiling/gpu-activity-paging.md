---
title: Aktywność procesora GPU (stronicowanie) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98917d9f0492a59b832d9e91da8f8e16059faae9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948794"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
**Aktywność procesora GPU (stronicowanie)** segmenty na **wątków** karcie reprezentują czas, po procesora GPU przetwarzającą żądania stronicowania.  Długość segmentu reprezentuje czas, czy procesor GPU przetwarzającą pakiet stronicowania dostępu (DMA) pamięci. Zazwyczaj stronicowania pakiety są skojarzone z transfer pamięci między GPU i CPU.  
  
 Po wybraniu segmentu stronicowania procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Obejmuje to ilość razem, gdy jego oczekiwania w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet DMA i czas wymagany do przetwarzania pakietów.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wykorzystania](../profiling/utilization-view.md)