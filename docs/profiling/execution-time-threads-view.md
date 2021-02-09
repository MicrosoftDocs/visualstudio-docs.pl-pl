---
title: Czas wykonywania (Widok wątków) | Microsoft Docs
description: Przejrzyj czas wykonywania w widoku wątków wizualizatora współbieżności. Czas wykonywania jest reprezentowany przez segmenty pokazujące, kiedy wątek aktywnie pracuje na rdzeniu logicznym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5c62c57e3037b38c2729917d2b882550b9c2d126
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861611"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty widoku wątki przedstawiają czas wykonywania, gdy wątek aktywnie wykonuje prace na logicznym rdzeń w systemie.

 Zmiany stanu wątku są wykrywane za poorednictwem zdarzeń przełącznika kontekstu jądra. Śledzenie zdarzeń systemu Windows (ETW) przechwytuje przykładowe stosy co milisekundy. W bardzo krótkim, zielonym segmencie jest możliwe, że nie jest pobierana żadna próba. W związku z tym niektóre krótkie segmenty wykonania mogą nie wyświetlać stosu wywołań.

 Po kliknięciu segmentu wykonywania, Wizualizator współbieżności Wyświetla przykładowy stos znajdujący się najbliżej lokalizacji kliknięcia. Położenie tego przykładowego stosu jest pokazane przez czarną strzałkę lub karetkę, nad osią czasu, a przykładowy stos pojawia się na **bieżącej** karcie.

 Aby wyświetlić tradycyjny profil próbkowania dla wszystkich segmentów wykonywania w bieżącym widoku, kliknij opcję **wykonywanie** w profilu widocznej osi czasu.

## <a name="see-also"></a>Zobacz też
- [Raport profilu wykonania](../profiling/execution-profile-report.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)