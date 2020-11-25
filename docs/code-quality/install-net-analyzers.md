---
title: Włącz lub zainstaluj analizatory .NET
ms.date: 08/03/2018
description: Dowiedz się, jak włączyć analizatory .NET z zestawu SDK platformy .NET lub zainstalować te analizatory jako pakiet NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112238"
---
# <a name="enable-or-install-net-analyzers"></a>Włącz lub zainstaluj analizatory .NET

## <a name="overview"></a>Omówienie

Analizatory platformy kompilatora .NET (Roslyn) sprawdzają kod C# lub Visual Basic pod kątem problemów dotyczących jakości i stylu. Można włączać lub instalować te analizatory w jeden z następujących sposobów:

- **Włącz z zestawu .NET SDK**: począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Analiza jest domyślnie włączona dla projektów przeznaczonych dla platformy .NET 5,0 lub nowszej. Możesz włączyć analizę kodu dla projektów przeznaczonych dla wcześniejszych wersji .NET, ustawiając `EnableNETAnalyzers` Właściwość na `true` . Możesz również wyłączyć analizę kodu dla projektu, ustawiając wartość `EnableNETAnalyzers` na `false` .

- **Zainstaluj jako pakiet NuGet**: Możesz także zainstalować te analizatory, instalując `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) w programie Visual Studio 2019. Jeśli używasz programu Visual Studio 2017, zainstaluj najnowszą `2.9.x` wersję `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakietu NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Zaleca się włączenie analizatorów z zestawu .NET SDK zamiast instalowania `Microsoft.CodeAnalysis.NetAnalyzers` [pakietu NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), jeśli jest to możliwe. Włączenie analizatorów z zestawu SDK platformy .NET gwarantuje, że podczas aktualizacji zestawu SDK automatycznie pobierzesz poprawki błędów i nowych analiz.

## <a name="see-also"></a>Zobacz też

- [Przegląd analizatorów kodu w programie Visual Studio](roslyn-analyzers-overview.md)
- [Korzystanie z analizatorów kodu w programie Visual Studio](use-roslyn-analyzers.md)
- [Migrowanie ze starszej analizy do analizatorów .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrowanie z analizatorów FxCop do analizatorów .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
