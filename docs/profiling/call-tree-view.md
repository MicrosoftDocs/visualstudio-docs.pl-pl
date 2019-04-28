---
title: Widok drzewa wywołań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c28ef62629011b222ae1a846c04cbf4cdff17d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440258"
---
# <a name="call-tree-view"></a>Widok drzewa wywołań
Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, nazwę i dane wydajności dotyczące tych wywołań funkcji.

 Widok drzewa wywołania można również rozwijać i Podświetlenie ścieżki wykonywania funkcji, która użyte najwięcej czasu lub zostało pobrane najczęściej. Aby wyświetlić najbardziej wydajności — kosztowne ścieżkę, kliknij prawym przyciskiem myszy funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**.

 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Możesz ustawić węzeł początkowy widoku drzewo wywołań prawym przyciskiem myszy węzeł, w której chcesz ustawić jako węzeł początkowy, a następnie wybierając **zestawu głównego**.

 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Możesz zresetować węzła głównego do węzła, który był wyświetlany. W oknie Widok drzewa wywołań, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **resetowania głównego**.

 Widok drzewa wywołania można dostosować w taki sposób, aby dodać lub usunąć kolumny. Kliknij prawym przyciskiem myszy **paska tytułu nazwę kolumny**, a następnie wybierz pozycję **Dodaj/Usuń kolumny**.

 Widok drzewa wywołania można skonfigurować dla obniżenia poziomu hałasu, ograniczając ilość danych, które są prezentowane. Za pomocą redukcji szumu, problemy z wydajnością, są lepiej widoczne w widoku. W przypadku łatwo odróżnić problemy z wydajnością analizy jest łatwiejsze. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie redukcji szumu w widokach raportu](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Jeśli redukcja szumów jest skonfigurowana do wyświetlania ostrzeżenia, gdy jest włączone, pasek informacji będą wyświetlane w raporcie.

 Aby uzyskać więcej informacji o definicjach kolumn w widoku drzewa wywołań zobacz następujące tematy:

- [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)

- [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)

- [Drzewo wywołań view - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Widok drzewa wywołań](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Zobacz także
- [Widoki raportu wydajności](../profiling/performance-report-views.md)
- [Zapoznanie z wartościami danych instrumentacji](../profiling/understanding-instrumentation-data-values.md)
- [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)