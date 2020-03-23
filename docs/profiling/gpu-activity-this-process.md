---
title: Aktywność gpu (ten proces) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969541"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
Segmenty **działania gpu (ten proces)** w widoku Wątki w wizualizatorze współbieżności reprezentują czasy, kiedy procesor GPU przetwarzał żądania w imieniu bieżącego procesu. Te żądania są wysyłane do gpu jako pakiety bezpośredniego dostępu do pamięci (DMA). Długość segmentu reprezentuje czas przetwarzania pakietu DMA przez procesor GPU w imieniu bieżącego procesu.

 Po wybraniu segmentu aktywności GPU w raporcie na karcie **Bieżący** są wyświetlane informacje o przetworzonym pakiecie DMA. Informacje te obejmują czas oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces przesyłania pakietu oraz czas wymagany do przetworzenia pakietu. Proces inny niż bieżący proces mógł fizycznie przesłać pakiet DMA do gpu. Wizualizator współbieżności można wykryć, gdy inny proces przesłane pracy do gpu w imieniu bieżącego procesu.