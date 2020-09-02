---
title: Aktywność procesora GPU (stronicowanie) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434166"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Segmenty **działania procesora GPU (stronicowania)** na karcie wątki przedstawiają czasy, kiedy procesor GPU przetwarza żądania stronicowania.  Długość segmentu reprezentuje czas, przez który procesor GPU przetworzył pakiet stronicowania bezpośredniego dostępu do pamięci (DMA). Zazwyczaj pakiety stronicowania są skojarzone z transferem pamięci między procesorem CPU a procesorem GPU.  
  
 Po wybraniu segmentu stronicowania procesora GPU raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie DMA. Obejmuje to czas oczekiwania w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet DMA, oraz czas wymagany do przetworzenia pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)
