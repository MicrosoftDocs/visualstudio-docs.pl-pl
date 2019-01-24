---
title: Czas wykonywania (Widok wątków) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766244"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu w widoku wątków reprezentują czas wykonywania, gdy wątek aktywnie wykonywania zadania na rdzeń logiczny w systemie.  
  
 Zmiany w stan wątku są wykrywane przez przekazywanie zdarzeń jądra kontekstu przełącznika. Śledzenie zdarzeń dla Windows (ETW) przechwytuje stosów próbka co milisekund. W bardzo krótkim zielonym segmencie możliwe jest nie pobraniu próbki. Dlatego niektóre segmentów wykonania na krótki mogą być wyświetlane żaden stos wywołań.  
  
 Po kliknięciu segmentu wykonania, Wizualizator współbieżności przedstawia przykładowy stos najbliższą lokalizację kliknięcie. Lokalizacja tego stosu próbki jest wyświetlany za pomocą czarne strzałki lub daszek powyżej osi czasu i Przykładowy stos jest wyświetlana na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjny dla wszystkich segmentów wykonania w bieżącym widoku, kliknij **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
