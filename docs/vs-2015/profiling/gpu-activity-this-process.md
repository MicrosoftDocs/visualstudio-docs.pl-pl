---
title: Aktywność procesora GPU (ten proces) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b616e307b3c42b09662be3fdad290ea9f740637c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434153"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Segmenty **działania procesora GPU (ten proces)** w widoku wątki w wizualizatorze współbieżności reprezentują czasy przetwarzania żądań procesora GPU w imieniu bieżącego procesu. Te żądania są wysyłane do procesora GPU jako pakiety bezpośredniego dostępu do pamięci (DMA). Długość segmentu reprezentuje czas przetwarzania pakietu przez procesor GPU w imieniu bieżącego procesu.  
  
 Po wybraniu segmentu aktywności procesora GPU raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie DMA. Te informacje obejmują ilość czasu oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet, oraz czas wymagany do przetworzenia pakietu. Proces inny niż bieżący proces może fizycznie przesłać pakiet DMA do procesora GPU. Wizualizator współbieżności może wykryć, kiedy inny proces został przesłany do procesora GPU w imieniu bieżącego procesu.
