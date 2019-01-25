---
title: Znaczniki zakresu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f733ccec12e422a11532b8012836422d14d93b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798036"
---
# <a name="span-markers"></a>Znaczniki zakresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Span znacznik reprezentuje fazę istotnych aplikacji. Na przykład można użyć zakres reprezentujący przedział czasu, w którym jest przetwarzany danego elementu pracy. Jego długość reprezentuje czas trwania określonego etapu aplikacji. Ta ilustracja przedstawia zakres w Wizualizatorze współbieżności:  
  
 ![Span znacznika w Wizualizatorze współbieżności](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Span znacznika w Wizualizatorze współbieżności  
  
## <a name="span-category"></a>Kategoria zakresu  
 Znacznik zakresu jest wyświetlany w jednej z pięciu różnych kolorach, w zależności od jego kategorii. Kolory są powtarzane, jeśli istnieje więcej niż pięć kategorii. Kategoria może być liczbą całkowitą. Ta ilustracja przedstawia pięć możliwych kolorów:  
  
 ![Pięć zakresy w różnych kategoriach](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Kolory pierwszych pięć kategorii zakresu  
  
## <a name="span-aggregation-markers"></a>Agregacja znaczniki zakresu  
 Czasami zakresu znaczniki wystąpić tak blisko siebie nawzajem w Wizualizatorze współbieżności, że nie można ich indywidualnie rysowania. Jeśli ten problem wystąpi, szary *znacznika zakresu agregacji* czy reprezentuje podstawowy zakresy jest widoczne. Po umieszczeniu wskaźnika na jednym z tych ikon etykietka narzędzia Wyświetla liczbę podstawowych zakresy, które są reprezentowane. Aby przejrzeć zakresy, powiększania. Jeśli powiększyć aż i nadal się pojawiać znacznika zakresu agregacji, można wyświetlić podstawowy znaczników zakresu w [raport dotyczący znaczników](../profiling/markers-report.md). Ta ilustracja przedstawia znacznika zakresu agregacji:  
  
 ![Wartość zagregowana span znacznika w Wizualizatorze współbieżności](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Znacznik zakresu agregacji  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)   
 [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)
