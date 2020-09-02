---
title: Aktywność procesora GPU (inne procesy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434140"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Segmenty **działania procesora GPU (inne procesy)** w widoku wątki wizualizatora współbieżności przedstawiają czasy, kiedy procesor GPU przetwarzał żądania w imieniu innych procesów w systemie. Te żądania są wysyłane przez procesor GPU jako pakiety bezpośredniego dostępu do pamięci (DMA).  Długość segmentu reprezentuje czas, przez który pakiet został przetworzony przez procesor GPU.  
  
 Po wybraniu tego rodzaju segmentu raport na **bieżącej** karcie zawiera informacje o przetworzonym pakiecie.  Informacje obejmują ilość czasu oczekiwania pakietu w kolejce sprzętowej skojarzonej z aparatem DirectX, proces, który przesłał pakiet, oraz czas wymagany do przetworzenia pakietu.
