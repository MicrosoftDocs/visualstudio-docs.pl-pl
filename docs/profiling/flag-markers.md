---
title: Znaczniki flagi | Microsoft Docs
description: Więcej informacji na temat znaczników flag znajduje się w programie Visual Studio Concurrency Visualizer. Znacznik flagi reprezentuje element, który wystąpił w czasie w aplikacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc7b128915b7fc961b44aa7d70a24a813d432ddf
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801473"
---
# <a name="flag-markers"></a>Znaczniki flagi
Znacznik flagi reprezentuje element, który wystąpił w czasie w aplikacji. Flaga może reprezentować wiele rodzajów zdarzeń aplikacji. Na przykład Flaga może pokazać, gdy określony element roboczy został zaplanowany lub wystąpił wyjątek. Środowiska uruchomieniowe, takie jak Biblioteka zadań równoległych, mogą również generować flagi.

## <a name="flag-importance"></a>Ważność flagi
 Flagi są wyświetlane w różnych rozmiarach w zależności od ich ważności. Podobnie jak w przypadku dowolnego znacznika ważność może mieć wartość niski, normalny, wysoki lub krytyczny.  Na tej ilustracji przedstawiono wygląd znaczników według poziomu ważności:

 ![Najważniejsze, normalne, wysokie i krytyczne znaczniki ważności](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") Znaczniki pokazujące ważność flagi

## <a name="flag-category"></a>Kategoria flagi
 Flaga jest wyświetlana w jednym z pięciu różnych kolorów, w zależności od jej kategorii. Kolory są ponownie używane, jeśli istnieje więcej niż pięć kategorii. Nie można wybrać koloru. Podobnie jak w przypadku dowolnego znacznika, Kategoria może być dowolną liczbą całkowitą. Następna ilustracja przedstawia kolory dla pierwszych pięciu kategorii.

 ![Pięć kolorów znaczników kategorii](../profiling/media/cvmarkercategory.png "CVMarkerCategory") Znaczniki pokazujące kategorie

## <a name="alerts"></a>Alerty
 Alert jest flagą czerwoną, która reprezentuje krytyczne zdarzenie aplikacji, na przykład wyjątek.  Oto Alert:

 ![Znacznik alertu Concurrency Visualizer](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Znacznik alertu

## <a name="aggregation-flags"></a>Flagi agregacji
 Czasami flagi następują blisko siebie w wizualizatorze współbieżności, że nie mogą być narysowane pojedynczo. W takim przypadku jest wyświetlana szara *Flaga agregacji* reprezentująca flagi bazowe. Po umieszczeniu wskaźnika na jednej z tych ikon etykietka narzędzia wyświetla liczbę podstawowych flag, które są reprezentowane. Aby wyświetlić flagi, Powiększ. W przypadku powiększania wszystkich sposobów i nadal uzyskania flagi agregacji, można wyświetlić flagi bazowe w [raporcie znaczniki](../profiling/markers-report.md).

 Flagi agregacji są rysowane w różnych rozmiarach. Rozmiar zależy od poziomu ważności flagi najważniejsze w agregacji. Na poniższej ilustracji przedstawiono flagi agregacji w celu zwiększenia ważności.

 ![Agreguj flagi przedstawiające cztery poziomy ważności](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Flagi agregacji według poziomu ważności

## <a name="see-also"></a>Zobacz także
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)