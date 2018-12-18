---
title: Aktywność procesora GPU (stronicowanie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cba0335a7090bc8f7308d5a64e8fedebedd99a6e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789931"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktywność procesora GPU (stronicowanie)** segmentów na karcie wątków reprezentują czas, kiedy procesora GPU zostało przetwarzania żądań stronicowania.  Długość segmentu reprezentuje czas, czy procesor GPU przetwarzającą pakiet stronicowania dostępu (DMA) pamięci. Zazwyczaj stronicowania pakiety są skojarzone z transfer pamięci między GPU i CPU.  
  
 Po wybraniu segmentu stronicowania procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Obejmuje to ilość razem, gdy jego oczekiwania w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet DMA i czas wymagany do przetwarzania pakietów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)



