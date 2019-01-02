---
title: Aktywność procesora GPU (inne procesy) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 570e5d313b6246903f5e6a931b10f33fa40bf3ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913413"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
**Aktywność procesora GPU (inne procesy)** segmenty w widoku wątków narzędzia Concurrency visualizer reprezentują czas, kiedy procesora GPU przetwarzającą żądania w imieniu innych procesów w systemie. Te żądania są wysyłane przez GPU jako pakiety dostępu (DMA) pamięci.  Długość segmentu reprezentuje czas przetwarzania pakietu przez GPU.  
  
 Po wybraniu tego rodzaju segmentu, raport na **bieżącego** karta zawiera informacje o pakiecie, która została przetworzona.  Informacje obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów.