---
title: Widok rdzeni | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b26b913a42a563e0226ff2697b947684dfec53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553061"
---
# <a name="cores-view"></a>Widok rdzeni
**Widok rdzeni** pokazuje, jak wykonanie wątku zostało mapowane na rdzenie procesora logicznego (wybierz **opcję Analizuj** > **wizualizator współbieżności,** aby uruchomić wizualizator współbieżności). Jeśli piszesz aplikacje serwera, ten widok może pomóc zoptymalizować wydajność pamięci podręcznej przy użyciu koligacji wątków lub zarządzania pulą wątków. Może również pomóc zbadać przypadki, w których użycie koligacji wątku może pogorszyć problem migracji międzyrdzeniowej. Widok rdzeni ma dwie części, wykres i legendę.

 Wykres przedstawia rdzenie logiczne na osi y i czasie na osi x. Każdy wątek na wykresie ma unikalny kolor, dzięki czemu można śledzić jego ruch w poprzek rdzeni w czasie. Wątki na tym wykresie można filtrować, zaznaczając je w obszarze legendy.

 Obszar legendy ma wpis dla każdego koloru na wykresie. Każdy wpis pokazuje kolor i nazwę wątku, liczbę przełączników kontekstu między rdzeniami, całkowitą liczbę przełączników kontekstu i procent przełączników kontekstu, które przecinają rdzenie. Legenda jest sortowana według liczby przełączników kontekstu między rdzeniami w kolejności malejącej. Wyświetla tylko wątki, które zostały wykonane podczas wyświetlanego zakresu czasu.  Lista zostanie zaktualizowana po powiększeniu lub przesunienie.

## <a name="see-also"></a>Zobacz też
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
- [Widok wykorzystania](../profiling/utilization-view.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)