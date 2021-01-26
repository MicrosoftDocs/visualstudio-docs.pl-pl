---
title: Aktywność procesora GPU (ten proces) | Microsoft Docs
description: Przeczytaj informacje o aktywności procesora GPU (ten proces) w widoku wątki wizualizatora współbieżności.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fcfc96f9b29b8fae3bf9a97273ed6c675d1655fb
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801167"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
Segmenty **działania procesora GPU (ten proces)** w widoku wątki w wizualizatorze współbieżności reprezentują czasy przetwarzania żądań procesora GPU w imieniu bieżącego procesu. Te żądania są wysyłane do procesora GPU jako pakiety bezpośredniego dostępu do pamięci (DMA). Długość segmentu reprezentuje czas przetwarzania pakietu przez procesor GPU w imieniu bieżącego procesu.

 Po wybraniu segmentu aktywności procesora GPU raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie DMA. Te informacje obejmują ilość czasu oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet, oraz czas wymagany do przetworzenia pakietu. Proces inny niż bieżący proces może fizycznie przesłać pakiet DMA do procesora GPU. Wizualizator współbieżności może wykryć, kiedy inny proces został przesłany do procesora GPU w imieniu bieżącego procesu.