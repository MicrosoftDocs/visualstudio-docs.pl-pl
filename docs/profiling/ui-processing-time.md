---
title: Czas przetwarzania interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f34bb5396c1cadeab7c02c72f8ed13412e33b0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858941"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako przetwarzania interfejsu użytkownika. Oznacza to, że wątek jest przekazywanie komunikatów Windows lub wykonywania innych zadań interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który zlicza Concurrency Visualizer jako przetwarzania interfejsu użytkownika. Interfejsy API, takie jak `GetMessage()` i `MsgWaitForMultipleObjects()` należą do tej grupy.  
  
 Jeśli zostanie zidentyfikowana żadnych wstępnie zdefiniowanych interfejsów API do blokowania, zapoznaj się z stosów wywołań i raportów profilu, aby ustalić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika pomoże Ci zrozumieć, czas reakcji aplikacji GUI i jest pożądane w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji realizuje 100% czasu przetwarzania interfejsu użytkownika, jest prawdopodobnie dynamiczny. Jednak jeśli wątek interfejsu użytkownika zużywa znaczną ilość czasu w innych kategoriach, poszukaj głównych przyczyn i należy rozważyć opcje redukcji kategorii bez interfejsu użytkownika dla tego wątku.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)