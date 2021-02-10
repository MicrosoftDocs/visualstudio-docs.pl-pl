---
title: Widok rdzeni | Microsoft Docs
description: Dowiedz się więcej o informacjach dostarczonych przez Widok rdzeni. Może on ułatwić korzystanie z koligacji wątków lub zarządzania pulą wątków w celu optymalizowania wydajności pamięci podręcznej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4f04fd5021e0ac11cd04e2e04df96da19af1c77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951670"
---
# <a name="cores-view"></a>Widok rdzeni
**Widok rdzeni** pokazuje, jak wykonywanie wątku zostało zamapowane na rdzenie procesora logicznego (wybierz polecenie **Analizuj**  >  **Wizualizator współbieżności** , aby uruchomić Wizualizator współbieżności). W przypadku pisania aplikacji serwerowych ten widok może pomóc zoptymalizować wydajność pamięci podręcznej za pomocą koligacji wątków lub zarządzania pulą wątków. Może również pomóc w sprawdzeniu przypadków, w których użycie koligacji wątku mogło spowodować problem z migracją między rdzeniami. Widok rdzeni ma dwie części, wykres i legendę.

 Wykres przedstawia rdzenie logiczne na osi y i godzinę na osi x. Każdy wątek na grafie ma unikatowy kolor, aby można było śledzić jego przenoszenie między rdzeniami w czasie. Możesz filtrować wątki na tym grafie, zaznaczając je w obszarze legendy.

 Obszar legendy zawiera wpis dla każdego koloru na grafie. Każdy wpis przedstawia kolor i nazwę wątku, liczbę przełączeń kontekstu między rdzeniami, całkowitą liczbę przełączeń kontekstu i procent przełączeń kontekstu między rdzeniami. Legenda jest sortowana według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej. Wyświetla listę tylko wątków, które są wykonywane w trakcie wyświetlanego zakresu czasu.  Lista jest aktualizowana w przypadku powiększania lub kadrowania.

## <a name="see-also"></a>Zobacz też
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
- [Widok wykorzystania](../profiling/utilization-view.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)