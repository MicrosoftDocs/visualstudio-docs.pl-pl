---
title: Aktywność procesora GPU (ten proces) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801690"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktywności procesora GPU (ten proces)** segmenty w widoku wątków w Wizualizatorze współbieżności reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pakiety dostępu (DMA) pamięci. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietu DMA imieniu bieżącego procesu.  
  
 Po wybraniu segmentu działanie procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzie Concurrency Visualizer można wykrywać przesyłanej przez inny proces roboczy do procesora GPU w imieniu bieżący proces.
