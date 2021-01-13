---
title: Widok drzewa wywołań | Microsoft Docs
description: Zapoznaj się z widokiem drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji.
ms.custom: SEO-VS-2020
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386f8e85c02fe73eab9801b3edf79ec0d0b178fc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150785"
---
# <a name="call-tree-view"></a>Widok drzewa wywołań
W widoku drzewa wywołań są wyświetlane ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich wywoływanych funkcji i danych wydajności dotyczących tych wywołań funkcji.

 Widok drzewa wywołań może również rozszerzać i wyróżniać ścieżkę wykonywania funkcji, która zużywa najwięcej czasu lub była najczęściej próbkowana. Aby wyświetlić najbardziej wydajną ścieżkę, kliknij ją prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz polecenie **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Możesz zresetować węzeł główny z powrotem do węzła, który był oglądany. W oknie widok drzewa wywołań kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Zresetuj katalog główny**.

 Widok drzewa wywołań można dostosować w celu dodania lub usunięcia kolumn. Kliknij prawym przyciskiem myszy **pasek tytułu nazw kolumn**, a następnie wybierz polecenie **Dodaj/Usuń kolumny**.

 Widok drzewa wywołań można skonfigurować pod kątem obniżenia poziomu hałasu przez ograniczenie ilości prezentowanych danych. Dzięki zmniejszeniu szumu problemy z wydajnością są bardziej widoczne w widoku. Gdy problemy z wydajnością można łatwo rozróżnić, analiza jest łatwiejsza. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie redukcji szumu w widokach raportu](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> W przypadku skonfigurowania obniżenia poziomu szumu w celu wyświetlenia ostrzeżenia po włączeniu tego raportu zostanie wyświetlony pasek informacji.

 Aby uzyskać więcej informacji na temat definicji kolumn w widoku drzewa wywołań, zobacz następujące tematy:

- [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)

- [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)

- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Widok drzewa wywołań](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Zobacz także
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
- [Zapoznanie z wartościami danych instrumentacji](../profiling/understanding-instrumentation-data-values.md)
- [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)
