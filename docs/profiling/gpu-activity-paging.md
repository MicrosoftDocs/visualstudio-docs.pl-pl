---
title: Aktywność gpu (stronicowanie) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969618"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
Segmenty **aktywności gpu (stronicowania)** na karcie Wątki reprezentują **czasy** przetwarzania żądań stronicowania przez procesor GPU.  Długość segmentu reprezentuje czas, przez który procesor GPU przetwarzał pakiet stronicowania dostępu do pamięci bezpośredniej (DMA). Zazwyczaj pakiety stronicowania są skojarzone z transferem pamięci między procesorem CPU a procesorem GPU.

 Po wybraniu segmentu stronicowania gpu raport na karcie **Bieżący** wyświetla informacje o przetworzonym pakiecie DMA. Obejmuje to czas oczekiwania w kolejce sprzętu skojarzonej z aparatem DirectX, proces, który przesłał pakiet DMA i czas wymagany do przetworzenia pakietu.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)