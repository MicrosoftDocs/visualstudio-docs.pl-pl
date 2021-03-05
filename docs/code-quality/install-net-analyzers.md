---
title: Włącz lub zainstaluj analizatory .NET pierwszej firmy
ms.date: 08/03/2018
description: Dowiedz się, jak włączyć analizatory .NET pierwszej firmy z zestawu SDK platformy .NET lub zainstalować te analizatory jako pakiet NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 368fd5bc9c8b7e2659c86b6e3dc69a609da37617
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144666"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Włącz lub zainstaluj analizatory .NET pierwszej firmy

## <a name="overview"></a>Omówienie

Analizatory platformy kompilatora .NET (Roslyn) sprawdzają kod C# lub Visual Basic pod kątem problemów dotyczących jakości i stylu. Analizatory .NET pierwszej firmy to **Target-platform niezależny od**. Oznacza to, że projekt nie musi być przeznaczony dla konkretnej platformy .NET. Analizatory współpracują z projektami przeznaczonymi do pracy, `net5.0` a także ze starszymi wersjami platformy .NET, takimi jak `netcoreapp` , `netstandard` i `net472` .

Analizatory .NET pierwszej jednostki można włączać lub instalować w jeden z następujących sposobów:

- **Włącz z zestawu .NET SDK**: począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Analiza jest domyślnie włączona dla projektów przeznaczonych dla platformy .NET 5,0 lub nowszej. Możesz włączyć analizę kodu dla projektów przeznaczonych dla wcześniejszych wersji .NET, ustawiając właściwość MSBUILD [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) na `true` . Możesz również wyłączyć analizę kodu dla projektu, ustawiając wartość `EnableNETAnalyzers` na `false` .

- **Zainstaluj jako pakiet NuGet**: Jeśli nie chcesz przenosić do programu .NET 5 lub zestawu SDK lub wolisz model oparty na pakiecie NuGet, analizatory są również dostępne w `Microsoft.CodeAnalysis.NetAnalyzers` [pakiecie NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) w programie Visual Studio 2019.  Można preferować model oparty na pakiecie dla aktualizacji wersji na żądanie. Jeśli korzystasz z programu Visual Studio 2017, `2.9.x` zamiast tego zainstaluj najnowszą wersję `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakietu NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) .

> [!NOTE]
> Zaleca się włączenie analizatorów z zestawu .NET SDK zamiast instalowania `Microsoft.CodeAnalysis.NetAnalyzers` [pakietu NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), jeśli jest to możliwe. Włączenie analizatorów z zestawu SDK platformy .NET gwarantuje, że podczas aktualizacji zestawu SDK automatycznie pobierzesz poprawki błędów i nowych analiz. W modelu NuGet należy zaktualizować pakiet NuGet za każdym razem, gdy chcesz użyć najnowszych poprawek błędów. Pakiet NuGet jest aktualizowany częściej.

## <a name="see-also"></a>Zobacz też

- [Przegląd analizatorów kodu w programie Visual Studio](roslyn-analyzers-overview.md)
- [Korzystanie z analizatorów kodu w programie Visual Studio](use-roslyn-analyzers.md)
- [Przechodzenie z analiz w starszej wersji na analizatory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Przechodzenie z analizatorów FxCop na analizatory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
