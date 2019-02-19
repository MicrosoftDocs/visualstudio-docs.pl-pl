---
title: Widok podsumowania — dane próbkowania | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8570692ec620ee50cd24f3fa95ceec8b21172919
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803088"
---
# <a name="summary-view---sampling-data"></a>Widok podsumowania — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok podsumowania Wyświetla informacje na temat wydajności najdroższych funkcji w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem powiadomienie łącza i listy raportów, zobacz [Widok Podsumowanie](../profiling/summary-view.md).  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku podsumowania przedstawia wartość procentową wykorzystania procesora (CPU) profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania. Wykres osi czasu można użyć do filtrowania widoku, aby w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak: Filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Ścieżka aktywna  
 **Ścieżka aktywna** wyświetla to ścieżka wykonania, w którym większość próbek. Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla tej funkcji. Aby wyświetlić inne widoki dotyczące funkcji, kliknij prawym przyciskiem myszy funkcję, a następnie kliknij widok z listy.  
  
 **Ścieżka aktywna** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Włącznych próbek**|Procent wszystkie przykłady, które wystąpiły podczas wykonywania tej funkcji i funkcji wywoływanych przez tę funkcję.|  
|**% Wyłącznych próbek**|Procent wszystkie przykłady, które wystąpiły podczas wykonywania kodu funkcji w treści funkcji. Przykłady zebrane w funkcjach wywoływanych przez tę funkcję, nie są uwzględniane.|  
  
## <a name="functions-doing-most-individual-work"></a>Funkcje wykonujące najwięcej indywidualnej pracy  
 **Funkcji wykonywania najbardziej samodzielnej pracy** lista zawiera funkcje, które mają największą liczbę próbek wyłącznych podczas uruchomienia profilowania. Próbek wyłącznych jest przypisany do funkcji, jeśli funkcja jest wykonywana swój własny kod w momencie próbki zostały zebrane. Próbek wyłącznych nie jest przypisany do funkcji, jeśli funkcja wywołuje inną funkcję, gdy zostały zebrane próbki. Duża liczba próbek wyłącznych wskazuje, że znaczną ilość czasu spędzono w samej funkcji.  
  
 Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla tej funkcji. Aby wyświetlić inne widoki dotyczące funkcji kliknij prawym przyciskiem myszy funkcję, a następnie kliknij widok z listy.  
  
 **Działa w sposób najbardziej samodzielnej pracy** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Wyłącznych próbek**|Procent wszystkich przykładów podczas uruchomienia profilowania, które zostały zebrane podczas wykonywania kodu funkcji w jego treści funkcji. Wartość procentowa wyklucza przykładów, które zostały zebrane podczas wykonywania zostały funkcje, które wywołuje tę funkcję.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)
