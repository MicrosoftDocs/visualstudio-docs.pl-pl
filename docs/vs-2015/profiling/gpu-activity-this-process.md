---
title: Aktywność procesora GPU (ten proces) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1b0949a71dc4db1ee217d691d4aae7928faf301
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751405"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktywności procesora GPU (ten proces)** segmenty w widoku wątków w Wizualizatorze współbieżności reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pakiety dostępu (DMA) pamięci. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietu DMA imieniu bieżącego procesu.  
  
 Po wybraniu segmentu działanie procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzie Concurrency Visualizer można wykrywać przesyłanej przez inny proces roboczy do procesora GPU w imieniu bieżący proces.



