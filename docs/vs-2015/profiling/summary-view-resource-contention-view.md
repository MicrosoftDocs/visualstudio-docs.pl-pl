---
title: Widok podsumowania — Widok rywalizacji o zasoby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65f659b64b6a1e29e1e25ae344dd8033e631de09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157770"
---
# <a name="summary-view---resource-contention-view"></a>Widok podsumowania — widok rywalizacji o zasoby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania zawiera informacje o zdarzeniach w aplikacji, w których wątek lub proces został wstrzymany podczas oczekiwania na dostęp do zasobu.  
  
 Aby uzyskać więcej informacji, w tym opis linków powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku Podsumowanie przedstawia liczbę zdarzeń rywalizacji profilowanej aplikacji w czasie, w którym wystąpiło profilowanie. Możesz użyć wykresu osi czasu do filtrowania widoku do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [How to: Filter viewss Reports from a Summary oś czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Zasoby z największą rywalizacją  
 **Zasoby z największą** rywalizacją zawierają listę zasobów w aplikacji, które spowodowały najwięcej zdarzeń związanych ze spisem. Możesz kliknąć nazwę zasobu, aby wyświetlić widok rywalizacji. Widok rywalizacji zawiera szczegółową oś czasu rywalizacji o zasoby według wątku.  
  
 **Zasoby z największą** ilością zasobów obejmują następujące dane dla każdego zasobu.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa zasobu.|  
|**Rywalizacji**|Wartość procentowa wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacjami za ten zasób.|  
  
## <a name="most-contended-thread"></a>Wątek z największą rywalizacją  
 **Wątki z największą** liczbą zdarzeń w programie wyświetlają wątki w aplikacji, które miały największą liczbę zdarzenia rywalizacji. Można kliknąć nazwę wątku, aby wyświetlić widok rywalizacji, który zapewnia szczegółową oś czasu rywalizacji o zasoby przez wątek.  
  
 **Wątki z największą** ilością ofert obejmują następujące dane dla każdego wątku.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**ID**|Identyfikator wątku.|  
|**Nazwa**|Nazwa procesu, który jest właścicielem wątku.|  
|**Rywalizacji**|Wartość procentowa wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacjami za ten zasób.|
