---
title: Czas wykonania (widok wątków) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0cf2a60fd194176b7cd9091f4e7dc7a758006f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969917"
---
# <a name="execution-time-threads-view"></a>Czas wykonania (widok wątków)
Te segmenty w wątki Widok osi czasu reprezentują czas wykonywania, gdy wątek aktywnie wykonuje pracę na rdzeniu logicznym w systemie.

 Zmiany stanu wątku są wykrywane za pomocą zdarzeń przełączania kontekstu jądra. Śledzenie zdarzeń dla systemu Windows (ETW) przechwytuje stosy próbek co milisekundę. W bardzo krótkim zielonym segmencie możliwe jest, że nie zostanie pobrana żadna próbka. W związku z tym niektóre segmenty wykonywania krótkie mogą wykazywać brak stosu wywołań.

 Po kliknięciu segmentu wykonania wizualizator współbieżności wyświetla stos próbki najbliżej lokalizacji kliknięcia. Lokalizacja tego stosu próbek jest wyświetlana przez czarną strzałkę lub cieszkę nad osią czasu, a stos próbek pojawi się na karcie **Bieżący.**

 Aby wyświetlić tradycyjny profil próbkowania dla wszystkich segmentów wykonania w bieżącym widoku, kliknij opcję **Wykonanie** w profilu widocznej osi czasu.

## <a name="see-also"></a>Zobacz też
- [Raport profilu wykonania](../profiling/execution-profile-report.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)