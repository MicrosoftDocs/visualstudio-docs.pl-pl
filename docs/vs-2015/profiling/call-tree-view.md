---
title: Widok drzewa wywołań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f09b85c20d84cb25d6a1fdbbd8493c47056318a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738749"
---
# <a name="call-tree-view"></a>Widok drzewa wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, nazwę i dane wydajności dotyczące tych wywołań funkcji.  
  
 Widok drzewa wywołania można również rozwijać i Podświetlenie ścieżki wykonywania funkcji, która użyte najwięcej czasu lub zostało pobrane najczęściej. Aby wyświetlić najbardziej wydajności — kosztowne ścieżkę, kliknij prawym przyciskiem myszy funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**.  
  
 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Możesz ustawić węzeł początkowy widoku drzewo wywołań prawym przyciskiem myszy węzeł, w której chcesz ustawić jako węzeł początkowy, a następnie wybierając **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Możesz zresetować węzła głównego do węzła, który był wyświetlany. W oknie Widok drzewa wywołań, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **resetowania głównego**.  
  
 Widok drzewa wywołania można dostosować w taki sposób, aby dodać lub usunąć kolumny. Kliknij prawym przyciskiem myszy **paska tytułu nazwę kolumny**, a następnie wybierz pozycję **Dodaj/Usuń kolumny**.  
  
 Widok drzewa wywołania można skonfigurować dla obniżenia poziomu hałasu, ograniczając ilość danych, które są prezentowane. Za pomocą redukcji szumu, problemy z wydajnością, są lepiej widoczne w widoku. W przypadku łatwo odróżnić problemy z wydajnością analizy jest łatwiejsze. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie redukcji szumu w widokach raportu](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Jeśli redukcja szumów jest skonfigurowana do wyświetlania ostrzeżenia, gdy jest włączone, pasek informacji będą wyświetlane w raporcie.  
  
 Aby uzyskać więcej informacji o definicjach kolumn w widoku drzewa wywołań zobacz następujące tematy:  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Widok drzewa wywołań — Próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Widok drzewa wywołań](../profiling/call-tree-view-contention-data.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki raportu wydajności](../profiling/performance-report-views.md)   
 [Zapoznanie z wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)   
 [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)



