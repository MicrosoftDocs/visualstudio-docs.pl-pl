---
title: Flaga znaczniki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19ecac740035cc6de49a5651b20f2408eddd27ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986829"
---
# <a name="flag-markers"></a>Znaczniki typu Flaga
Znacznik flagi reprezentuje coś, który wystąpił na moment w czasie w aplikacji. Flaga może reprezentować wiele rodzajów zdarzeń aplikacji. Na przykład flagę można pokazać, kiedy zostało zaplanowane danego elementu pracy, lub gdy wystąpił wyjątek. Środowiska uruchomieniowe, takich jak biblioteka zadań równoległych, można również wygenerować flag.  
  
## <a name="flag-importance"></a>Flaga znaczenie  
 Flagi są wyświetlane w różnych rozmiarach, w zależności od ich znaczenia. Podobnie jak wszelkie znacznika znaczenie może być niska, normalna, wysoką lub krytyczne.  Ta ilustracja przedstawia wygląd znaczników przez poziom ważności:  
  
 ![Niska, normalna, o wysokiej i krytyczne znaczniki znaczenie](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Znaczniki przedstawiający znaczenie flagi  
  
## <a name="flag-category"></a>Flaga kategorii  
 Flaga jest wyświetlany w jednej z pięciu różnych kolorach, w zależności od jego kategorii. Kolory są używane ponownie, jeśli istnieje więcej niż pięć kategorii. Nie można wybrać kolor. Podobnie jak wszelkie znacznika kategorii może być liczbą całkowitą. Następna ilustracja przedstawia kolory dla pierwszych pięć kategorii.  
  
 ![Pięć kolory znaczników kategorii](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Znaczniki wyświetlane kategorie  
  
## <a name="alerts"></a>Alerty  
 Alert jest flagę kolorowe czerwony, która reprezentuje zdarzenie aplikacja o krytycznym znaczeniu, takich jak wyjątek.  Oto alert:  
  
 ![Znacznik alertu wizualizatora współbieżności](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Znacznik alertu  
  
## <a name="aggregation-flags"></a>Flagi agregacji  
 Flagi wystąpić tak blisko siebie nawzajem w Wizualizatorze współbieżności, że nie można ich indywidualnie rysowania. Jeśli ten problem wystąpi, szary *flagi agregacji* czy reprezentuje flagi podstawowej jest widoczne. Po umieszczeniu wskaźnika na jednym z tych ikon etykietka narzędzia Wyświetla liczbę podstawowych flagi, które są reprezentowane. Aby wyświetlić flagi, powiększania. Jeśli powiększyć aż, a mimo to uzyskać flagi agregacji, można wyświetlić podstawowy flagi w [raport dotyczący znaczników](../profiling/markers-report.md).  
  
 Flagi agregacji są rysowane w różnych rozmiarach. Rozmiar zależy od poziomu ważności najważniejszych flagi agregacji. Poniższej ilustracji przedstawiono flagi agregacji w rosnącej kolejności ważności.  
  
 ![Wartość zagregowana flagi przedstawiający cztery poziomy ważności](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Flagi agregacji przez poziom ważności  
  
## <a name="see-also"></a>Zobacz także  
 [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)   
 [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)