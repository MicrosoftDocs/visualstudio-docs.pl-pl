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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a502590c20fce1455d9259ae681178d9cd48e33
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624155"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
**Aktywność procesora GPU (inne procesy)** segmenty w widoku wątków narzędzia Concurrency visualizer reprezentują czas, kiedy procesora GPU przetwarzającą żądania w imieniu innych procesów w systemie. Te żądania są wysyłane przez GPU jako pakiety dostępu (DMA) pamięci.  Długość segmentu reprezentuje czas przetwarzania pakietu przez GPU.

 Po wybraniu tego rodzaju segmentu, raport na **bieżącego** karta zawiera informacje o pakiecie, która została przetworzona.  Informacje obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów.