---
title: Czas wykonywania (Widok wątków) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4131b70a0d76f5245152e397032f55833421c424
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905958"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty na osi czasu w widoku wątków reprezentują czas wykonywania, gdy wątek aktywnie wykonywania zadania na rdzeń logiczny w systemie.  
  
 Zmiany w stan wątku są wykrywane przez przekazywanie zdarzeń jądra kontekstu przełącznika. Śledzenie zdarzeń dla Windows (ETW) przechwytuje stosów próbka co milisekund. W bardzo krótkim zielonym segmencie możliwe jest nie pobraniu próbki. Dlatego niektóre segmentów wykonania na krótki mogą być wyświetlane żaden stos wywołań.  
  
 Po kliknięciu segmentu wykonania, Wizualizator współbieżności przedstawia przykładowy stos najbliższą lokalizację kliknięcie. Lokalizacja tego stosu próbki jest wyświetlany za pomocą czarne strzałki lub daszek powyżej osi czasu i Przykładowy stos jest wyświetlana na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjny dla wszystkich segmentów wykonania w bieżącym widoku, kliknij **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz także  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)