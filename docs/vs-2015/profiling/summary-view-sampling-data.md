---
title: Widok podsumowania — dane próbkowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c759922fcd28ce0b686745fc917c02f41762cae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817982"
---
# <a name="summary-view---sampling-data"></a>Widok podsumowania — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania zawiera informacje o najbardziej wydajnych funkcjach w przebiegu profilowania. Aby uzyskać więcej informacji, w tym opis linków powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku Podsumowanie przedstawia procent użycia procesora (CPU) przez profilowaną aplikację w czasie, w którym nastąpiło profilowanie. Możesz użyć wykresu osi czasu do filtrowania widoku do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [How to: Filter viewss Reports from a Summary oś czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Ścieżka gorąca  
 **Ścieżka gorąca** wyświetla ścieżkę wykonywania, w której zbierane są większość przykładów. Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla funkcji. Aby wyświetlić inne widoki dla funkcji, kliknij ją prawym przyciskiem myszy, a następnie kliknij Widok z listy.  
  
 **Ścieżka gorąca** zawiera następujące dane dla każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**Próbki włączne%**|Procent wszystkich próbek, które wystąpiły podczas wykonywania tej funkcji lub funkcji wywołanej przez tę funkcję.|  
|**Wyłącznych próbek%**|Procent wszystkich próbek, które wystąpiły, gdy funkcja wykonywała kod w treści funkcji. Próbki zebrane w funkcjach wywoływanych przez tę funkcję nie są uwzględniane.|  
  
## <a name="functions-doing-most-individual-work"></a>Funkcje wykonujące najwięcej indywidualnej pracy  
 **Funkcje wykonujące najwięcej poszczególnych list roboczych** wyświetlają funkcje, które mają największą liczbę próbek wyłącznych w przebiegu profilowania. W przypadku, gdy funkcja wykonuje własny kod podczas zbierania próbki, jest przypisywana do funkcji. Próbka wyłączna nie jest przypisana do funkcji, jeśli funkcja wywołuje inną funkcję podczas zbierania próbki. Duża liczba wyłącznych próbek wskazuje, że znaczny czas spędzony w samej funkcji.  
  
 Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla funkcji. Aby wyświetlić inne widoki dla funkcji, kliknij ją prawym przyciskiem myszy, a następnie kliknij Widok z listy.  
  
 **Funkcje wykonujące najwięcej indywidualnych zadań** obejmują następujące dane dla każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, który został zebrany, gdy funkcja wykonywała kod w jego treści funkcji. Wartość procentowa nie obejmuje próbek, które zostały zebrane, gdy funkcje, które zostały wywołane przez tę funkcję, były wykonywane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)
