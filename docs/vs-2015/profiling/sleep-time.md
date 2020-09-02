---
title: Czas uśpienia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198374"
---
# <a name="sleep-time"></a>Czas uśpienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako uśpienie. Kategoria uśpienia oznacza, że wątek jest dobrowolnie przeznaczony do jego rdzenia logicznego i nie działa. W tym czasie wątek został zablokowany w interfejsie API, który Wizualizator współbieżności zlicza jako uśpienie. Interfejsy API, takie jak `Sleep()` i `SwitchToThread()` mieszczą się w tej grupie.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
