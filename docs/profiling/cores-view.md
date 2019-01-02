---
title: Widok rdzeni | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dea7eca97ed938271977fea8e8fa5e41dbd19aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933706"
---
# <a name="cores-view"></a>Widok rdzeni
**Widoku rdzeni** pokazuje, jak wykonanie wątku został zamapowany na rdzeni procesora logicznego (wybierz **analizy** > **Concurrency Visualizer** do uruchomienia Narzędzie CONCURRENCY visualizer). Jeśli piszesz aplikacje serwera, ten widok może pomóc w optymalizacji wydajności pamięci podręcznej przy użyciu przystawki Zarządzanie puli wątków koligacji lub wątku. Może również pomóc możesz sprawdzić przypadki, w którym korzystanie z koligacji wątku może mieć pogorszyła problem migracji między różnymi rdzeniami. Widok rdzeni ma dwie części, wykresu i legenda.  
  
 Na wykresie widać rdzenie logiczne na osi y i godziny na osi x. Każdy wątek na wykresie ma unikatowy kolor, więc możliwe jest śledzenie jego ruchu między rdzeniami wraz z upływem czasu. Wątki na tym wykresie można filtrować, wybierając je w obszarze legendy.  
  
 W obszarze legendy ma wpis dla każdego koloru na wykresie. Każdy wpis zawiera kolor wątku i nazwę, liczba przełączeń kontekstu między rdzeniami, całkowita liczba przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Legendy są posortowane według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej. Wyświetla listę wątków, które wykonywane w czasie wyświetlane.  Lista jest aktualizowana, jeśli użytkownik przybliżanie/Oddalanie lub przesuwanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)