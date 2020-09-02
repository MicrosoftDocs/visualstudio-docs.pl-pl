---
title: Aktywność procesora GPU (inne procesy) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969505"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
Segmenty **działania procesora GPU (inne procesy)** w widoku wątki wizualizatora współbieżności przedstawiają czasy, kiedy procesor GPU przetwarzał żądania w imieniu innych procesów w systemie. Te żądania są wysyłane przez procesor GPU jako pakiety bezpośredniego dostępu do pamięci (DMA).  Długość segmentu reprezentuje czas, przez który pakiet został przetworzony przez procesor GPU.

 Po wybraniu tego rodzaju segmentu raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie.  Informacje obejmują ilość czasu oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet, oraz czas wymagany do przetworzenia pakietu.