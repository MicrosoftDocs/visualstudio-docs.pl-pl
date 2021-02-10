---
title: Wizualizator współbieżności | Microsoft Docs
description: Użyj wizualizatora współbieżności, aby zobaczyć wykresy pokazujące chronometraż wątku w aplikacji wielowątkowej, pomagając w rozwiązywaniu problemów z wydajnością.
ms.custom: SEO-VS-2020
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: becd44d5f7c5a28681d5fd180689909086b23c89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941063"
---
# <a name="concurrency-visualizer"></a>Concurrency Visualizer

> [!NOTE]
> Wizualizator współbieżności jest opcjonalnym rozszerzeniem programu Visual Studio. Pobierz narzędzie Concurrency Visualizer i narzędzia kolekcji Concurrency Visualizer z następujących linków:
>
> - Pobierz rozszerzenie [Concurrency Visualizer dla rozszerzenia programu Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview) .
> - Pobierz rozszerzenie [Concurrency Visualizer dla rozszerzenia programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) .
> - Pobierz rozszerzenie [Concurrency Visualizer dla rozszerzenia programu Visual Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) .
> - Pobierz [Narzędzia do zbierania danych Concurrency Visualizer dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> [Narzędzie Command-Line narzędzia Concurrency Visualizer (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umożliwia zbieranie śladów z wiersza polecenia, które można wyświetlić w programie Concurrency Visualizer dla programu Visual Studio 2015. Narzędzia można używać na komputerach, na których nie zainstalowano programu Visual Studio.

Możesz użyć wizualizatora współbieżności, aby zobaczyć, jak działa aplikacja wielowątkowa. Widoki w wizualizatorze współbieżności zapewniają dane graficzne, tabelaryczne i tekstowe, które pokazują relacje czasowe między wątkami w programie i systemem jako całością. Można użyć wizualizatora współbieżności do lokalizowania wąskich gardeł wydajności, niedostatecznego wykorzystania procesora, rywalizacji wątków, migracji wątków międzyrdzeniowych, opóźnień synchronizacji, aktywności DirectX, obszarów nakładających się operacji we/wy i innych informacji. Widoki zawierają dane, które można wykonywać, łącząc ich graficzne dane wyjściowe z stosami wywołań i kodem źródłowym.

> [!NOTE]
> Wizualizator współbieżności nie obsługuje projektów sieci Web.

Wizualizator współbieżności korzysta z funkcji [śledzenia zdarzeń dla systemu Windows](/windows/win32/etw/event-tracing-portal) .

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Widok wykorzystania](../profiling/utilization-view.md)|Opisuje sposób wyświetlania i analizowania aktywności systemu na wszystkich procesorach.|
|[Widok wątków](../profiling/threads-view-parallel-performance.md)|Opisuje sposób analizowania interakcji między wątkami w programie.|
|[Widok rdzeni](../profiling/cores-view.md)|Opisuje sposób analizowania migracji wątków między rdzeniami.|
|[Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Opisuje kilka typowych wzorców i pokazuje, jak pojawiają się one w wizualizatorze współbieżności.|
|[Programowanie równoległe w blogu programu Visual Studio](/archive/blogs/visualizeparallel/)|Zawiera wskazówki i najlepsze rozwiązania dotyczące wizualizatora współbieżności.|
|[Widoki raportu wydajności](../profiling/performance-report-views.md)|Zawiera informacje referencyjne dotyczące raportów i widoków narzędzia profilowania programu Visual Studio.|
|[Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)|Opisuje sposób Instrumentacji kodu źródłowego do wyświetlania dodatkowych informacji w wizualizatorze współbieżności.|
|[Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Opisuje, jak używać narzędzia wiersza polecenia Concurrency Visualizer (CVCollectionCmd.exe) do zbierania i przetwarzania śladów na maszynach, które nie mają programu Visual Studio.|

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)