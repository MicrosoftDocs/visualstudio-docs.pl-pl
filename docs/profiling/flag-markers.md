---
title: Znaczniki flagi | Dokumenty firmy Microsoft
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
ms.openlocfilehash: ccc0c7aa3386e906ad13331a596953db70240701
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969970"
---
# <a name="flag-markers"></a>Znaczniki flagi
Znacznik flagi reprezentuje coś, co wystąpiło w jednej chwili w aplikacji. Flaga może reprezentować wiele rodzajów zdarzeń aplikacji. Na przykład flaga może pokazać, kiedy zaplanowano określony element pracy lub gdy został zgłoszony wyjątek. Środowiska wykonawcze, takie jak biblioteka równoległa zadań, mogą również generować flagi.

## <a name="flag-importance"></a>Znaczenie flagi
 Flagi są wyświetlane w różnych rozmiarach w zależności od ich znaczenia. Jak każdy znacznik, znaczenie może być niskie, normalne, wysokie lub krytyczne.  Na ilustracji przedstawiono wygląd znaczników według poziomu ważności:

 ![Znaczniki niskiego, normalnego, wysokiego i krytycznego](../profiling/media/cvmarkerimportance.png "CvMarkerImportance") Znaczniki z ważnością flagi

## <a name="flag-category"></a>Kategoria flagi
 Flaga jest wyświetlana w jednym z pięciu różnych kolorów w zależności od jej kategorii. Kolory są ponownie używane, jeśli istnieje więcej niż pięć kategorii. Nie można wybrać koloru. Jak każdy znacznik, kategoria może być dowolną całkowitej liczby. Na następnej ilustracji przedstawiono kolory dla pierwszych pięciu kategorii.

 ![Pięć kolorów znaczników kategorii](../profiling/media/cvmarkercategory.png "Kategoria CVMarker") Znaczniki przedstawiające kategorie

## <a name="alerts"></a>Alerty
 Alert jest flagą w kolorze czerwonym, która reprezentuje zdarzenie aplikacji krytyczne, takie jak wyjątek.  Oto alert:

 ![Znacznik alertu wizualizatora współbieżności](../profiling/media/cvmarkeralert.png "Identyfikator CVMarkerAlert") Znacznik alertu

## <a name="aggregation-flags"></a>Flagi agregacji
 Czasami flagi występują tak blisko siebie w wizualizatora współbieżności, że nie można ich rysować indywidualnie. W takim przypadku wyświetlana jest *szara flaga agregacji* reprezentująca flagi źródłowe. Po umieszczeniu wskaźnika na jednej z tych ikon, etykietka narzędzia wyświetla liczbę flag źródłowych, które są reprezentowane. Aby wyświetlić flagi, powiększ. Jeśli powiększysz cały sposób i nadal otrzymujesz flagę agregacji, możesz wyświetlić flagi źródłowe w [raporcie znaczników](../profiling/markers-report.md).

 Flagi agregacji są rysowane w różnych rozmiarach. Rozmiar zależy od poziomu ważności najważniejszej flagi w agregacji. Na poniższej ilustracji przedstawiono flagi agregacji w rosnącej kolejności ważności.

 ![Agregowane flagi z czterema poziomami ważności](../profiling/media/cvmarkeraggregate.png "CvMarkerZagregat") Flagi agregacji według poziomu ważności

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)