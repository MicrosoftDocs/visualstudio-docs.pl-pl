---
title: Znaczniki zakresu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69b48a5b1b551e2e29b9aa10e7f68ff0df0e379
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980981"
---
# <a name="span-markers"></a>Znaczniki zakresu
Span znacznik reprezentuje fazę istotnych aplikacji. Na przykład można użyć zakres reprezentujący przedział czasu, w którym jest przetwarzany danego elementu pracy. Jego długość reprezentuje czas trwania określonego etapu aplikacji. Ta ilustracja przedstawia zakres w Wizualizatorze współbieżności:

 ![Span znacznika w Wizualizatorze współbieżności](../profiling/media/cvmarkerspan.png "CVMarkerSpan") zakresu znacznika w Wizualizatorze współbieżności

## <a name="span-category"></a>Kategoria zakresu
 Znacznik zakresu jest wyświetlany w jednej z pięciu różnych kolorach, w zależności od jego kategorii. Kolory są powtarzane, jeśli istnieje więcej niż pięć kategorii. Kategoria może być liczbą całkowitą. Ta ilustracja przedstawia pięć możliwych kolorów:

 ![Pięć zakresy w różnych kategoriach](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") kolory pierwszych pięć kategorii zakresu

## <a name="span-aggregation-markers"></a>Agregacja znaczniki zakresu
 Czasami zakresu znaczniki wystąpić tak blisko siebie nawzajem w Wizualizatorze współbieżności, że nie można ich indywidualnie rysowania. Jeśli ten problem wystąpi, szary *znacznika zakresu agregacji* czy reprezentuje podstawowy zakresy jest widoczne. Po umieszczeniu wskaźnika na jednym z tych ikon etykietka narzędzia Wyświetla liczbę podstawowych zakresy, które są reprezentowane. Aby przejrzeć zakresy, powiększania. Jeśli powiększyć aż i nadal się pojawiać znacznika zakresu agregacji, można wyświetlić podstawowy znaczników zakresu w [raport dotyczący znaczników](../profiling/markers-report.md). Ta ilustracja przedstawia znacznika zakresu agregacji:

 ![Wartość zagregowana span znacznika w Wizualizatorze współbieżności](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") znacznika zakresu agregacji

## <a name="see-also"></a>Zobacz także
- [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)
- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)