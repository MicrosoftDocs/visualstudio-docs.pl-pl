---
title: Czas uśpienia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980216"
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako uśpienie. Kategoria uśpienia oznacza, że wątek jest dobrowolnie przeznaczony do jego rdzenia logicznego i nie działa. W tym czasie wątek został zablokowany w interfejsie API, który Wizualizator współbieżności zlicza jako uśpienie. Interfejsy API, takie jak `Sleep()` i `SwitchToThread()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)