---
title: Jednoczesne używanie wielu narzędzi profilera | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332041"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Jednoczesne używanie wielu narzędzi profilera

Profiler wydajności został zaprojektowany z myślą o tym, że w tej samej sesji można używać wielu narzędzi, aby pomóc w zrozumieniu problemów z wydajnością. Większość narzędzi w profilerze wydajności obsługuje współbieżne uruchamianie, takie jak [użycie procesora CPU](../profiling/cpu-usage.md), [Narzędzie asynchroniczne platformy .NET](../profiling/analyze-async.md)i narzędzie [Database](../profiling/analyze-database.md) . Aby uruchamiać narzędzia jednocześnie w ramach tej samej sesji diagnostycznej, kliknij pole wyboru obok nich, a następnie Rozpocznij sesję diagnostyczną.

![Wybrano wszystkie narzędzia w centrum diag](../profiling/media/diaghuballtoolsselected.png "Wybrano wszystkie narzędzia w centrum diag")

>[!NOTE]
>Niektóre narzędzia, takie jak narzędzie [alokacji obiektów .NET](../profiling/dotnet-alloc-tool.md) , nie mogą być uruchamiane z innymi narzędziami ze względu na ich duże obciążenie lub z powodu innych ograniczeń technicznych.

## <a name="time-filtering"></a>Filtrowanie czasu 

Podczas analizy operacje filtrowania czasu są stosowane między narzędziami, dzięki czemu można użyć informacji w jednym narzędziu, aby zawęzić zakres czasu i odfiltrować dane w innym narzędziu. Ta funkcja ułatwia analizę do określonych punktów w śledzeniu i pomaga zrozumieć stan aplikacji.

![Filtrowanie czasu centrum diag](../profiling/media/diaghubtimefiltering.png "Filtrowanie czasu centrum diag")

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie ustawień profilera](../profiling/optimize-profiler-settings.md)
- [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Zapoznanie z metodami zbierania danych wydajności](../profiling/understanding-performance-collection-methods-perf-profiler.md)
