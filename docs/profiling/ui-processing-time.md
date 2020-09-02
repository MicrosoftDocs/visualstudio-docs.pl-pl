---
title: Czas przetwarzania interfejsu użytkownika | Microsoft Docs
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
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "63004454"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako przetwarzanie interfejsu użytkownika. Oznacza to, że wątek jest pompą komunikatów systemu Windows lub wykonywania innych czynności interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który jest obliczany przez Wizualizator współbieżności jako przetwarzanie interfejsu użytkownika. Interfejsy API, takie jak `GetMessage()` i `MsgWaitForMultipleObjects()` mieszczą się w tej grupie.

 Jeśli nie określono wstępnie zdefiniowanego interfejsu API blokowania, przejrzyj stosy wywołań i raporty profilu, aby określić podstawowe przyczyny opóźnienia.

 Kategoria przetwarzanie interfejsu użytkownika pomaga zrozumieć czas reakcji aplikacji GUI i jest pożądana w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji uzyskuje 100% czasu w czasie przetwarzania interfejsu użytkownika, prawdopodobnie odpowiada. Jeśli jednak wątek interfejsu użytkownika spędza znaczący czas w innych kategoriach, należy poszukać głównych przyczyn i rozważyć Opcje zmniejszenia kategorii innych niż interfejs użytkownika w tym wątku.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)