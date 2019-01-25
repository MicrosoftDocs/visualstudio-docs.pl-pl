---
title: Widok podsumowania — widok Kontencji zasobów | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804111"
---
# <a name="summary-view---resource-contention-view"></a>Widok podsumowania — widok rywalizacji o zasoby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania Wyświetla informacje o zdarzeniach w Twojej aplikacji, w którym wątku lub procesu zostało wstrzymane, podczas gdy oczekiwano dostęp do zasobu.  
  
 Aby uzyskać więcej informacji, łącznie z opisem powiadomienie łącza i listy raportów, zobacz [Widok Podsumowanie](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku podsumowania przedstawia liczbę zdarzeń rywalizacji o zasoby w profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania. Wykres osi czasu można użyć do filtrowania widoku, aby w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak: Filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Zasoby z największą rywalizacją  
 **Większość zasobów z rywalizacją** zawiera listę zasobów w aplikacji, która spowodowała najbardziej zdarzenia rywalizacji. Kliknięcie nazwy zasobu, aby wyświetlić widok rywalizacji. Widok Kontencji zapewnia szczegółowe oś czasu rywalizacji zasobów przez wątek.  
  
 **Większość zasobów z rywalizacją** zawiera następujące dane dla każdego zasobu.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa zasobu.|  
|**% Rywalizacji**|Procent wszystkich zdarzeń rywalizacji o zasoby w danych profilowania, które były rywalizacji za pośrednictwem tego zasobu.|  
  
## <a name="most-contended-thread"></a>Najbardziej rywalizacją wątku  
 **Większość wątków z rywalizacją** Wyświetla listę wątków w aplikacji, która ma największą liczbę zdarzeń rywalizacji o zasoby. Kliknięcie nazwy wątku, aby wyświetlić widok rywalizacji, który dostarcza szczegółowe oś czasu rywalizacji zasobów przez wątek.  
  
 **Większość wątków z rywalizacją** zawiera następujące dane dla każdego wątku.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator**|Identyfikator wątku.|  
|**Nazwa**|Nazwa procesu, który jest właścicielem wątku.|  
|**% Rywalizacji**|Procent wszystkich zdarzeń rywalizacji o zasoby w danych profilowania, które były rywalizacji za pośrednictwem tego zasobu.|
