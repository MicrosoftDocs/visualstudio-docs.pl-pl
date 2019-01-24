---
title: Aktywność procesora GPU (stronicowanie) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769099"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktywność procesora GPU (stronicowanie)** segmentów na karcie wątków reprezentują czas, kiedy procesora GPU zostało przetwarzania żądań stronicowania.  Długość segmentu reprezentuje czas, czy procesor GPU przetwarzającą pakiet stronicowania dostępu (DMA) pamięci. Zazwyczaj stronicowania pakiety są skojarzone z transfer pamięci między GPU i CPU.  
  
 Po wybraniu segmentu stronicowania procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Obejmuje to ilość razem, gdy jego oczekiwania w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet DMA i czas wymagany do przetwarzania pakietów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)
