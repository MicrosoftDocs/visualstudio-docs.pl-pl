---
title: Znaczniki rozpiętości | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62980981"
---
# <a name="span-markers"></a>Znaczniki zakresu
Znacznik zakresu reprezentuje znaczącą fazę aplikacji. Na przykład można użyć zakresu do reprezentowania interwału czasu, podczas którego jest przetwarzany określony element pracy. Jego długość reprezentuje czas trwania odpowiedniej fazy aplikacji. Na tej ilustracji przedstawiono zakres w wizualizatorze współbieżności:

 ![Znacznik rozpiętości w wizualizatorze współbieżności](../profiling/media/cvmarkerspan.png "CvMarkerSpan (Polski)") Znacznik rozpiętości w wizualizatorze współbieżności

## <a name="span-category"></a>Kategoria zakresu
 Znacznik zakresu jest wyświetlany w jednym z pięciu różnych kolorów, w zależności od kategorii. Kolory są powtarzane, jeśli istnieje więcej niż pięć kategorii. Kategoria może być dowolną całkowitej liczby. Na ilustracji przedstawiono pięć możliwych kolorów:

 ![Pięć przęseł w różnych kategoriach](../profiling/media/cvmarkerspancategory.png "Kategoria CVMarkerSpan") Kolory pierwszych pięciu kategorii zakresu

## <a name="span-aggregation-markers"></a>Znaczniki agregacji zakresu
 Czasami znaczniki zakresu występują tak blisko siebie w wizualizatora współbieżności, że nie można ich rysować indywidualnie. W takim przypadku wyświetlany jest *znacznik agregacji zakresu szarego* reprezentującego podstawowe zakresy. Po umieszczeniu wskaźnika na jednej z tych ikon, etykietka narzędzia wyświetla liczbę podstawowych zakresów, które są reprezentowane. Aby wyświetlić zakresy, powiększ. Jeśli powiększysz cały czas i nadal otrzymujesz znacznik agregacji zakresu, możesz wyświetlić podstawowe znaczniki zakresu w [raporcie znaczników](../profiling/markers-report.md). Na ilustracji przedstawiono znacznik agregacji zakresu:

 ![Znacznik zakresu agregacji w wizualizatorze współbieżności](../profiling/media/cvmarkerspanaggregate.png "CvMarkerSpanAgregat") Znacznik agregacji zakresu

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)