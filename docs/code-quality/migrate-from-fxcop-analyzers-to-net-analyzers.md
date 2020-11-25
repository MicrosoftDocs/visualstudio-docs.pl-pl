---
title: Migrowanie z analizatorów FxCop do analizatorów .NET
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112250"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrowanie z analizatorów FxCop do analizatorów .NET

Analiza źródła według .NET Compiler Platform ("Roslyn") analizatory zamieniają [starszą analizę](code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Wiele reguł starszej analizy (FxCop) zostało już zapisaną jako analizatory źródła.

W systemach starszych niż Visual Studio 2019 16,8 i .NET 5,0 te analizatory są dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Pakiet NuGet wkrótce będzie przestarzały.

## <a name="migration-steps"></a>Kroki migracji

Wykonaj poniższe kroki, aby przeprowadzić migrację projektu lub rozwiązania z programu `Microsoft.CodeAnalysis.FxCopAnalyzers` do analizatorów .NET:

1. Odinstaluj `Microsoft.CodeAnalysis.FxCopAnalyzers` pakiet NuGet

2. [Włącz lub zainstaluj analizatory .NET](install-net-analyzers.md)

3. Włącz dodatkowe reguły: `Microsoft.CodeAnalysis.NetAnalyzers` jest znacznie bardziej ostrożne w porównaniu z `Microsoft.CodeAnalysis.FxCopAnalyzers` . W przeciwieństwie do pakietu FxCopAnalyzers, ma tylko kilka reguł poprawności, które są [domyślnie włączone jako ostrzeżenia kompilacji](/dotnet/fundamentals/code-analysis/overview#enabled-rules). [Dodatkowe reguły można włączyć](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) przez dostosowanie [Właściwości programu](/dotnet/core/project-sdk/msbuild-props#analysismode) msbuildmode. Na przykład ustawienie właściwości na wartość `AllEnabledByDefault` spowoduje włączenie wszystkich odpowiednich reguł urzędu certyfikacji jako ostrzeżeń kompilacji.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Zobacz też

- [Analiza kodu źródłowego w porównaniu do starszej analizy](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrowanie ze starszej analizy do analizatorów .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Włącz lub zainstaluj analizatory .NET](install-net-analyzers.md)
- [Często zadawane pytania dotyczące analizatorów .NET](net-analyzers-faq.md)
- [Konfigurowanie analizatorów .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
