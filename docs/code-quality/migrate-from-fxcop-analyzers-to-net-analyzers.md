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
ms.openlocfilehash: e435502587e65bd694567f4100516a91fa97cc0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867870"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Przechodzenie z analizatorów FxCop na analizatory .NET

Analiza źródła według .NET Compiler Platform ("Roslyn") analizatory zamieniają [starszą analizę](code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Wiele reguł starszej analizy (FxCop) zostało już zapisaną jako analizatory źródła.

W systemach starszych niż Visual Studio 2019 16,8 i .NET 5,0 te analizatory są dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jeśli nie chcesz przenosić do programu .NET 5 lub SDK lub wolisz model oparty na pakiecie NuGet, analizatory są również dostępne w `Microsoft.CodeAnalysis.NetAnalyzers` [pakiecie NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Można preferować model oparty na pakiecie dla aktualizacji wersji na żądanie.

> [!NOTE]
> Analizatory .NET pierwszej firmy to target-platform niezależny od. Oznacza to, że projekt nie musi być przeznaczony dla konkretnej platformy .NET. Analizatory współpracują z projektami przeznaczonymi do pracy, `net5.0` a także ze starszymi wersjami platformy .NET, takimi jak `netcoreapp` , `netstandard` i `net472` .

## <a name="migration-steps"></a>Kroki migracji

Począwszy od wersji `3.3.2` , `Microsoft.CodeAnalysis.FxCopAnalyzers` pakiet NuGet został uznany za przestarzały. Wykonaj poniższe kroki, aby przeprowadzić migrację projektu lub rozwiązania z programu `Microsoft.CodeAnalysis.FxCopAnalyzers` do analizatorów .NET:

1. Odinstaluj `Microsoft.CodeAnalysis.FxCopAnalyzers` pakiet NuGet

2. [Włącz lub zainstaluj analizatory platformy .NET](install-net-analyzers.md). Należy pamiętać, że nie trzeba zmieniać platformy docelowej projektu.

3. Włącz dodatkowe reguły: `Microsoft.CodeAnalysis.NetAnalyzers` jest znacznie bardziej ostrożne w porównaniu z `Microsoft.CodeAnalysis.FxCopAnalyzers` . W przeciwieństwie do pakietu FxCopAnalyzers, ma tylko kilka reguł poprawności, które są [domyślnie włączone jako ostrzeżenia kompilacji](/dotnet/fundamentals/code-analysis/overview#enabled-rules). [Dodatkowe reguły można włączyć](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) przez dostosowanie [Właściwości programu](/dotnet/core/project-sdk/msbuild-props#analysismode) msbuildmode. Na przykład ustawienie właściwości na wartość `AllEnabledByDefault` spowoduje włączenie wszystkich odpowiednich reguł urzędu certyfikacji jako ostrzeżeń kompilacji.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Zobacz też

- [Analiza kodu źródłowego w porównaniu do starszej analizy](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Przechodzenie z analiz w starszej wersji na analizatory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Włącz lub zainstaluj analizatory .NET](install-net-analyzers.md)
- [Często zadawane pytania dotyczące analizatorów .NET](net-analyzers-faq.md)
- [Konfigurowanie analizatorów .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
