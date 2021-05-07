---
title: Przechodzenie z analizatorów FxCop na analizatory .NET
ms.custom: SEO-VS-2020
description: Dowiedz się, jak przeprowadzić migrację z analizatorów FxCop do analizatorów .NET
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798261"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Przechodzenie z analizatorów FxCop na analizatory .NET

Analiza źródła .NET Compiler Platform analizatorów ("Roslyn") zastępuje [starszą analizę](code-analysis-for-managed-code-overview.md) kodu zarządzanego. Wiele starszych reguł analizy (FxCop) zostało już przepisanych jako analizatory źródła.

Przed Visual Studio 2019 r. 16.8 i .NET 5.0 te analizatory były dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Począwszy od Visual Studio 2019 r. 16.8 i .NET 5.0, te analizatory są dołączone do [zestawu SDK platformy .NET.](/dotnet/fundamentals/code-analysis/overview) Jeśli nie chcesz przechodzić do zestawu .NET 5+ SDK lub jeśli wolisz model oparty na pakiecie NuGet, analizatory są również dostępne w `Microsoft.CodeAnalysis.NetAnalyzers` [pakiecie NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). W przypadku aktualizacji wersji na żądanie może być preferowany model oparty na pakietach.

> [!NOTE]
> Analizatory platformy .NET są niezależne od platformy docelowej. Oznacza to, że projekt nie musi być ukierunkowany na określoną platformę .NET. Analizatory działają dla projektów docelowych, jak również wcześniejszych wersji `net5.0` .NET, takich jak , i `netcoreapp` `netstandard` `net472` .

## <a name="migration-steps"></a>Kroki migracji

Począwszy od `3.3.2` wersji , pakiet `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet jest przestarzały. Wykonaj poniższe kroki, aby przeprowadzić migrację projektu lub rozwiązania z `Microsoft.CodeAnalysis.FxCopAnalyzers` programu do analizatorów .NET:

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`Odinstalowywanie pakietu NuGet

2. [Włącz lub zainstaluj analizatory .NET.](install-net-analyzers.md) Pamiętaj, że nie musisz zmieniać platformy docelowej projektu.

3. Włącz dodatkowe reguły: `Microsoft.CodeAnalysis.NetAnalyzers` jest znacznie bardziej zachowawczy w porównaniu do `Microsoft.CodeAnalysis.FxCopAnalyzers` . W przeciwieństwie do pakietu FxCopAnalyzers ma tylko kilka reguł poprawności, które są domyślnie włączone [jako ostrzeżenia kompilacji](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Dodatkowe reguły [można włączyć przez](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) dostosowanie [właściwości AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild. Na przykład ustawienie właściwości na wartość spowoduje domyślne włączenie wszystkich odpowiednich reguł urzędu certyfikacji `AllEnabledByDefault` jako ostrzeżeń kompilacji.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Zobacz też

- [Analiza kodu źródłowego a starsza analiza](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Przechodzenie z analiz w starszej wersji na analizatory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Włączanie lub instalowanie analizatorów .NET](install-net-analyzers.md)
- [Często zadawane pytania dotyczące analizatorów .NET](net-analyzers-faq.yml)
- [Konfigurowanie analizatorów .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
