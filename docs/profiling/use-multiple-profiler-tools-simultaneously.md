---
title: Jednoczesne używanie wielu narzędzi profilera | Microsoft Docs
description: Dowiedz się, jak Profiler wydajności został zaprojektowany z myślą o tym, że w tej samej sesji można używać wielu narzędzi, aby pomóc w zrozumieniu problemów z wydajnością.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 5a4c4658282f15b6b34562e51be94d9f2be195a8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721180"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Jednoczesne używanie wielu narzędzi profilera

Profiler wydajności został zaprojektowany z myślą o tym, że w tej samej sesji można używać wielu narzędzi, aby pomóc w zrozumieniu problemów z wydajnością. Większość narzędzi w profilerze wydajności obsługuje współbieżne uruchamianie, takie jak [użycie procesora CPU](../profiling/cpu-usage.md), [Narzędzie asynchroniczne platformy .NET](../profiling/analyze-async.md)i narzędzie [Database](../profiling/analyze-database.md) . Aby uruchamiać narzędzia jednocześnie w ramach tej samej sesji diagnostycznej, kliknij pole wyboru obok nich, a następnie Rozpocznij sesję diagnostyczną.

![Wybrano wszystkie narzędzia w centrum diag](../profiling/media/diaghuballtoolsselected.png "Wybrano wszystkie narzędzia w centrum diag")

>[!NOTE]
>Niektóre narzędzia, takie jak narzędzie [alokacji obiektów .NET](../profiling/dotnet-alloc-tool.md) , nie mogą być uruchamiane z innymi narzędziami ze względu na ich duże obciążenie lub z powodu innych ograniczeń technicznych.

## <a name="time-filtering"></a>Filtrowanie czasu 

Podczas analizy operacje filtrowania czasu są stosowane między narzędziami, dzięki czemu można użyć informacji w jednym narzędziu, aby zawęzić zakres czasu i odfiltrować dane w innym narzędziu. Ta funkcja ułatwia analizę do określonych punktów w śledzeniu i pomaga zrozumieć stan aplikacji.

![Filtrowanie czasu centrum diag](../profiling/media/diaghubtimefiltering.png "Filtrowanie czasu centrum diag")

## <a name="see-also"></a>Zobacz także

- [Optymalizowanie ustawień profilera](../profiling/optimize-profiler-settings.md)
- [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Zapoznanie z metodami zbierania danych wydajności](../profiling/understanding-performance-collection-methods-perf-profiler.md)
