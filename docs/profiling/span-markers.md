---
title: Znaczniki zakresu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980981"
---
# <a name="span-markers"></a>Znaczniki zakresu
Znacznik span reprezentuje znaczącą fazę aplikacji. Na przykład można użyć zakresu, aby reprezentować przedział czasu, w którym jest przetwarzany konkretny element roboczy. Jego długość reprezentuje czas trwania odpowiedniej fazy aplikacji. Na tej ilustracji przedstawiono zakres w wizualizatorze współbieżności:

 ![Znacznik zakresu w wizualizatorze współbieżności](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Znacznik zakresu w wizualizatorze współbieżności

## <a name="span-category"></a>Kategoria zakresu
 Znacznik zakresu jest wyświetlany w jednym z pięciu różnych kolorów, w zależności od jego kategorii. Kolory są powtarzane, jeśli istnieje więcej niż pięć kategorii. Kategoria może być dowolną liczbą całkowitą. Na tej ilustracji przedstawiono pięć możliwych kolorów:

 ![Pięć zakresów w różnych kategoriach](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") Kolory pierwszych pięciu kategorii zakresu

## <a name="span-aggregation-markers"></a>Znaczniki agregacji zakresu
 Czasami znaczniki rozciągają się, aby blisko siebie w wizualizatorze współbieżności, które nie mogą być narysowane pojedynczo. W takim przypadku jest pokazywany szary *znacznik agregacji* , który reprezentuje bazowe zakresy. Po umieszczeniu wskaźnika na jednej z tych ikon, w etykietce narzędzia zostanie wyświetlona liczba przedstawionych podstawowych zakresów. Aby wyświetlić zakresy, Powiększ. W przypadku powiększania wszystkich sposobów i nadal uzyskiwania znacznika agregacji zakresu można wyświetlić bazowe znaczniki zakresu w [raporcie znaczniki](../profiling/markers-report.md). Na tej ilustracji przedstawiono znacznik agregacji zakresu:

 ![Znacznik zagregowanego zakresu w wizualizatorze współbieżności](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Znacznik agregacji zakresu

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)