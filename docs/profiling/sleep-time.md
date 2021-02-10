---
title: Czas uśpienia | Microsoft Docs
description: Zapoznaj się z tym, że Kategoria uśpienia oznacza, że wątek jest dobrowolnie określony jako rdzeń logiczny i nie działa.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a433d11c2684a4a39660759f33d49bd719c2b2ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960172"
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako uśpienie. Kategoria uśpienia oznacza, że wątek jest dobrowolnie przeznaczony do jego rdzenia logicznego i nie działa. W tym czasie wątek został zablokowany w interfejsie API, który Wizualizator współbieżności zlicza jako uśpienie. Interfejsy API, takie jak `Sleep()` i `SwitchToThread()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)