---
title: Aktywność procesora GPU (stronicowanie) | Microsoft Docs
description: Przejrzyj segmenty działania procesora GPU (stronicowanie) na karcie wątki wizualizatora współbieżności. Segmenty reprezentują czasy przetwarzania żądań stronicowania procesora GPU.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4467d2a885f4076461110fe288b4e80169158ede
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877099"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
Segmenty **działania procesora GPU (stronicowania)** na karcie **wątki** przedstawiają czasy, kiedy procesor GPU przetwarza żądania stronicowania.  Długość segmentu reprezentuje czas, przez który procesor GPU przetworzył pakiet stronicowania bezpośredniego dostępu do pamięci (DMA). Zazwyczaj pakiety stronicowania są skojarzone z transferem pamięci między procesorem CPU a procesorem GPU.

 Po wybraniu segmentu stronicowania procesora GPU raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie DMA. Obejmuje to czas oczekiwania w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet DMA, oraz czas wymagany do przetworzenia pakietu.

## <a name="see-also"></a>Zobacz też
- [Widok wykorzystania](../profiling/utilization-view.md)