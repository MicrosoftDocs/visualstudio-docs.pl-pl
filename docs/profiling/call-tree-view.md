---
title: Widok drzewa połączeń | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 0b932d5f9e4a178c94f3e490c66cec64648ce4f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773338"
---
# <a name="call-tree-view"></a>Widok drzewa wywołań
Widok Drzewa wywołań wyświetla ścieżki wykonywania funkcji, które zostały przesuniętych w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywołuje i dane wydajności o tych wywołań funkcji.

 Widok drzewa wywołań można również rozwinąć i wyróżnić ścieżkę wykonywania funkcji, która pochłonęła najwięcej czasu lub była najczęściej próbkowana. Aby wyświetlić najbardziej wydajną ścieżkę, kliknij tę funkcję prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Węzeł początkowy widoku Drzewo wywołań można ustawić, klikając prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierając **pozycję Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku z wyjątkiem poddrzewa wybranego węzła. Węzeł główny można zresetować z powrotem do przeglądanym węzłem. W oknie widoku Drzewo wywołań kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Resetuj katalog główny**.

 Widok Drzewa wywołań można dostosować, aby dodać lub usunąć kolumny. Kliknij prawym przyciskiem myszy **pasek tytułu nazwy kolumny,** a następnie wybierz polecenie **Dodaj/Usuń kolumny**.

 Widok Drzewa wywołań można skonfigurować w celu redukcji szumów, ograniczając ilość prezentowanych danych. Dzięki redukcji szumów problemy z wydajnością są bardziej widoczne w widoku. Gdy problemy z wydajnością są łatwe do odróżnienia, analiza jest łatwiejsza. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie redukcji szumów w widokach raportu](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Jeśli redukcja szumów jest skonfigurowana do wyświetlania ostrzeżenia, gdy jest włączone, w raporcie zostanie wyświetlony pasek informacji.

 Aby uzyskać więcej informacji na temat definicji kolumn w widoku Drzewa wywołań, zobacz następujące informacje:

- [Widok drzewa połączeń](../profiling/call-tree-view-sampling-data.md)

- [Widok drzewa połączeń](../profiling/call-tree-view-instrumentation-data.md)

- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Widok drzewa połączeń](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Zobacz też
- [Widoki raportu o skuteczności](../profiling/performance-report-views.md)
- [Zapoznanie z wartościami danych instrumentacji](../profiling/understanding-instrumentation-data-values.md)
- [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)
