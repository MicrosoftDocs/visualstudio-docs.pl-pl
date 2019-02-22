---
title: Aktywność procesora GPU (ten proces) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68e85fc44977a3d9756965de12e25d13d62dbb89
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625143"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
**Aktywności procesora GPU (ten proces)** segmenty w widoku wątków w Wizualizatorze współbieżności reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pakiety dostępu (DMA) pamięci. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietu DMA imieniu bieżącego procesu.

 Po wybraniu segmentu działanie procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzie Concurrency Visualizer można wykrywać przesyłanej przez inny proces roboczy do procesora GPU w imieniu bieżący proces.