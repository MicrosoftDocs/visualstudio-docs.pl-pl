---
title: Znaczniki flagi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e531d2d2a41cc9ceaa3b6ba39c6d77a166cfae83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193686"
---
# <a name="flag-markers"></a>Znaczniki typu flaga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znacznik flagi reprezentuje element, który wystąpił w czasie w aplikacji. Flaga może reprezentować wiele rodzajów zdarzeń aplikacji. Na przykład Flaga może pokazać, gdy określony element roboczy został zaplanowany lub wystąpił wyjątek. Środowiska uruchomieniowe, takie jak Biblioteka zadań równoległych, mogą również generować flagi.  
  
## <a name="flag-importance"></a>Ważność flagi  
 Flagi są wyświetlane w różnych rozmiarach w zależności od ich ważności. Podobnie jak w przypadku dowolnego znacznika ważność może mieć wartość niski, normalny, wysoki lub krytyczny.  Na tej ilustracji przedstawiono wygląd znaczników według poziomu ważności:  
  
 ![Najważniejsze, normalne, wysokie i krytyczne znaczniki ważności](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Znaczniki pokazujące ważność flagi  
  
## <a name="flag-category"></a>Kategoria flagi  
 Flaga jest wyświetlana w jednym z pięciu różnych kolorów, w zależności od jej kategorii. Kolory są ponownie używane, jeśli istnieje więcej niż pięć kategorii. Nie można wybrać koloru. Podobnie jak w przypadku dowolnego znacznika, Kategoria może być dowolną liczbą całkowitą. Następna ilustracja przedstawia kolory dla pierwszych pięciu kategorii.  
  
 ![Pięć kolorów znaczników kategorii](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Znaczniki pokazujące kategorie  
  
## <a name="alerts"></a>Alerty  
 Alert jest flagą czerwoną, która reprezentuje krytyczne zdarzenie aplikacji, na przykład wyjątek.  Oto Alert:  
  
 ![Znacznik alertu Concurrency Visualizer](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Znacznik alertu  
  
## <a name="aggregation-flags"></a>Flagi agregacji  
 Czasami flagi następują blisko siebie w wizualizatorze współbieżności, że nie mogą być narysowane pojedynczo. W takim przypadku jest wyświetlana szara *Flaga agregacji* reprezentująca flagi bazowe. Po umieszczeniu wskaźnika na jednej z tych ikon etykietka narzędzia wyświetla liczbę podstawowych flag, które są reprezentowane. Aby wyświetlić flagi, Powiększ. W przypadku powiększania wszystkich sposobów i nadal uzyskania flagi agregacji, można wyświetlić flagi bazowe w [raporcie znaczniki](../profiling/markers-report.md).  
  
 Flagi agregacji są rysowane w różnych rozmiarach. Rozmiar zależy od poziomu ważności flagi najważniejsze w agregacji. Na poniższej ilustracji przedstawiono flagi agregacji w celu zwiększenia ważności.  
  
 ![Agreguj flagi przedstawiające cztery poziomy ważności](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Flagi agregacji według poziomu ważności  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)   
 [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)
