---
title: Aktywność procesora GPU (inne procesy) | Microsoft Docs
description: Poznaj segmenty aktywności procesora GPU (inne procesy) w widoku wątki wizualizatora współbieżności.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71ecb1587545120aef8e18ce847d5e957f3e3cdd
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801318"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
Segmenty **działania procesora GPU (inne procesy)** w widoku wątki wizualizatora współbieżności przedstawiają czasy, kiedy procesor GPU przetwarzał żądania w imieniu innych procesów w systemie. Te żądania są wysyłane przez procesor GPU jako pakiety bezpośredniego dostępu do pamięci (DMA).  Długość segmentu reprezentuje czas, przez który pakiet został przetworzony przez procesor GPU.

 Po wybraniu tego rodzaju segmentu raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie.  Informacje obejmują ilość czasu oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet, oraz czas wymagany do przetworzenia pakietu.