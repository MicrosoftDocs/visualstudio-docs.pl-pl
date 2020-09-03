---
title: Czas wykonywania (Widok wątków) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179030"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty widoku wątki przedstawiają czas wykonywania, gdy wątek aktywnie wykonuje prace na logicznym rdzeń w systemie.  
  
 Zmiany stanu wątku są wykrywane za poorednictwem zdarzeń przełącznika kontekstu jądra. Śledzenie zdarzeń systemu Windows (ETW) przechwytuje przykładowe stosy co milisekundy. W bardzo krótkim, zielonym segmencie jest możliwe, że nie jest pobierana żadna próba. W związku z tym niektóre krótkie segmenty wykonania mogą nie wyświetlać stosu wywołań.  
  
 Po kliknięciu segmentu wykonywania, Wizualizator współbieżności Wyświetla przykładowy stos znajdujący się najbliżej lokalizacji kliknięcia. Położenie tego przykładowego stosu jest pokazane przez czarną strzałkę lub karetkę, nad osią czasu, a przykładowy stos pojawia się na **bieżącej** karcie.  
  
 Aby wyświetlić tradycyjny profil próbkowania dla wszystkich segmentów wykonywania w bieżącym widoku, kliknij opcję **wykonywanie** w profilu widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonywania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
