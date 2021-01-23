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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e66e62c2f7d78003581b12121844090c9754c2cc
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720062"
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z czasem blokowania, który jest kategoryzowany jako uśpienie. Kategoria uśpienia oznacza, że wątek jest dobrowolnie przeznaczony do jego rdzenia logicznego i nie działa. W tym czasie wątek został zablokowany w interfejsie API, który Wizualizator współbieżności zlicza jako uśpienie. Interfejsy API, takie jak `Sleep()` i `SwitchToThread()` mieszczą się w tej grupie.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)