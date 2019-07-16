---
title: Widok podsumowania - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc0b4195d33a7bf72d17681b6d71e78f1bacfe5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157778"
---
# <a name="summary-view---instrumentation-data"></a>Widok podsumowania — dane instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania Wyświetla informacje na temat wydajności najdroższych funkcji w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem powiadomienie łącza i listy raportów, zobacz [Widok Podsumowanie](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku podsumowania przedstawia użycie procesora (CPU) według profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania. Wykres osi czasu można użyć do filtrowania widoku, aby w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak: Filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Ścieżka aktywna  
 **Ścieżka aktywna** Wyświetla ścieżka wykonania, która używane najwięcej czasu. Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla tej funkcji. Aby wyświetlić inne widoki dotyczące funkcji kliknij prawym przyciskiem myszy funkcję, a następnie kliknij widok z listy.  
  
 **Ścieżka aktywna** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Całkowitego czasu, który upłynął**|Procent cały czas w danych profilowania, która funkcja poświęcony na wykonywanie kodu, w jego treści funkcji i funkcji, które je wywołuje.|  
|**% Wyłącznego czasu, który upłynął**|Procent cały czas w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas w funkcje, które wywołały funkcję nie jest włączony.|  
  
## <a name="functions-with-most-individual-work"></a>Funkcje z największą ilością indywidualnej pracy  
 Lista funkcji, które używane większość czasu wykonywania kodu w treści funkcji, a nie w funkcje, które go wywołały.  
  
 **Funkcje z najbardziej samodzielnej pracy** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Własnego czasu**|Procent cały czas w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas w funkcje, które wywołały funkcję nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)
