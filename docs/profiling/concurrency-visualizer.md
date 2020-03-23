---
title: Wizualizator współbieżności | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3b4e151db08ad5490ed6238223d553f9e76aa0f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77192406"
---
# <a name="concurrency-visualizer"></a>Concurrency Visualizer

> [!NOTE]
> Wizualizator współbieżności jest opcjonalnym rozszerzeniem programu Visual Studio. Pobierz wizualizator współbieżności i narzędzia do zbierania wizualizatorów współbieżności z następujących łączy:
>
> - Pobierz rozszerzenie [Wizualizator współbieżności dla programu Visual Studio 2019.](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview)
> - Pobierz rozszerzenie [Wizualizator współbieżności dla programu Visual Studio 2017.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview)
> - Pobierz rozszerzenie [Wizualizator współbieżności dla programu Visual Studio 2015.](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015)
> - Pobierz narzędzia do [zbierania obrazów współbieżności dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> [Narzędzie wiersza polecenia wizualizatora współbieżności (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umożliwia zbieranie śladów z wiersza polecenia, który można wyświetlić w wizualizatorze współbieżności dla programu Visual Studio 2015. Narzędzie może być używane na komputerach, na których nie zainstalowano programu Visual Studio.

Wizualizatora współbieżności można użyć, aby zobaczyć, jak działa aplikacja wielowątkowa. Widoki w wizualizatorze współbieżności zawierają dane graficzne, tabelaryczne i tekstowe, które pokazują czasowe relacje między wątkami w programie a systemem jako całością. Wizualizator współbieżności służy do lokalizowania wąskich gardeł wydajności, niedostatecznego wykorzystania procesora CPU, rywalizacji wątków, migracji wątków międzyrdzeniowych, opóźnień synchronizacji, aktywności DirectX, obszarów nakładających się we/wy i innych informacji. Widoki zawierają dane, które można działać na łącząc jego dane wyjściowe graficzne do wywołania stosy i kod źródłowy.

> [!NOTE]
> Wizualizator współbieżności nie obsługuje projektów sieci Web.

Wizualizator współbieżności opiera się na śledzenie zdarzeń dla funkcji [systemu Windows.](/windows/win32/etw/event-tracing-portal)

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Widok wykorzystania](../profiling/utilization-view.md)|W tym artykule opisano sposób wyświetlania i analizowania aktywności systemu we wszystkich procesorach.|
|[Widok wątków](../profiling/threads-view-parallel-performance.md)|W tym artykule opisano sposób analizowania interakcji między wątkami w programie.|
|[Widok rdzeni](../profiling/cores-view.md)|W tym artykule opisano sposób analizowania migracji wątków między rdzeniami.|
|[Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|W tym artykule opisano kilka typowych wzorców i pokazuje, jak pojawiają się one w wizualizatora współbieżności.|
|[Program równoległy w programie Visual Studio w blogu](https://blogs.msdn.microsoft.com/visualizeparallel/)|Zawiera porady i najlepsze rozwiązania dotyczące wizualizatora współbieżności.|
|[Widoki raportu wydajności](../profiling/performance-report-views.md)|Zawiera informacje referencyjne dla raportów i widoków narzędzi do profilowania programu Visual Studio.|
|[Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)|W tym artykule opisano sposób instrumentacji kodu źródłowego, aby wyświetlić dodatkowe informacje w wizualizatora współbieżności.|
|[Narzędzie wiersza polecenia wizualizatora współbieżności (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|W tym artykule opisano, jak używać narzędzia wiersza polecenia wizualizatora współbieżności (CVCollectionCmd.exe) do zbierania i przetwarzania śladów na komputerach, które nie mają programu Visual Studio.|

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
