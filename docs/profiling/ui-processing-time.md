---
title: Czas przetwarzania interfejsu użytkownika | Microsoft Docs
description: Dowiedz się, że segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako przetwarzanie interfejsu użytkownika.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63462aedfb1d7a2c03fe6ff5d59495358c52194e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722389"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako przetwarzanie interfejsu użytkownika. Oznacza to, że wątek jest pompą komunikatów systemu Windows lub wykonywania innych czynności interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który jest obliczany przez Wizualizator współbieżności jako przetwarzanie interfejsu użytkownika. Interfejsy API, takie jak `GetMessage()` i `MsgWaitForMultipleObjects()` mieszczą się w tej grupie.

 Jeśli nie określono wstępnie zdefiniowanego interfejsu API blokowania, przejrzyj stosy wywołań i raporty profilu, aby określić podstawowe przyczyny opóźnienia.

 Kategoria przetwarzanie interfejsu użytkownika pomaga zrozumieć czas reakcji aplikacji GUI i jest pożądana w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji uzyskuje 100% czasu w czasie przetwarzania interfejsu użytkownika, prawdopodobnie odpowiada. Jeśli jednak wątek interfejsu użytkownika spędza znaczący czas w innych kategoriach, należy poszukać głównych przyczyn i rozważyć Opcje zmniejszenia kategorii innych niż interfejs użytkownika w tym wątku.

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)