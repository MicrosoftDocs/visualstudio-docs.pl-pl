---
title: Migrowanie z aplikacji FxCop do analizy źródła (analizatory .NET)
ms.custom: SEO-VS-2020
description: Dowiedz się, jak analizować kod po raz pierwszy lub jak przeprowadzić migrację z analizy binarnej (FxCop) do nowego sposobu analizowania kodu zarządzanego przy użyciu analizy źródła (analizatory .NET).
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
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798235"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migracja ze starszej analizy (FxCop) do analizy źródła (analizatory .NET)

Analiza źródła przez .NET Compiler Platform ("Roslyn") zastępuje [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) kodu zarządzanego. W przypadku nowszej wersji szablonów projektów, takich jak .NET Core i .NET Standard projektów, starsza analiza nie jest dostępna.

Wiele starszych reguł analizy (FxCop) zostało już przepisanych dla analizatorów .NET, zestawu analizatorów kodu Roslyn. Analizatory Roslyn uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

Aby uzyskać więcej informacji na temat różnic między analizą w starszej wersji a analizą źródła, zobacz następujące informacje:

- [Analiza kodu źródłowego a starsza analiza](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [Często zadawane pytania dotyczące analizatorów .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Migracja

Aby przeprowadzić migrację do analizy źródła, [włącz lub zainstaluj analizatory .NET.](install-net-analyzers.md) Podobnie jak naruszenia starszych reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie Lista błędów w Visual Studio. Ponadto naruszenia analizy kodu źródłowego są również wyświetlane w edytorze kodu jako zygmki *pod* kodem naruszającym kod. Kolor zygzyka zależy od [ustawienia ważności](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) reguły. Aby wyświetlić stan reguł przenoszowanych do nowych analizatorów .NET, zobacz [Reguły portowane i nieimportowane.](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> Przed Visual Studio 2019 r. 16.8 i .NET 5.0 te analizatory były dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Począwszy od Visual Studio 2019 r. 16.8 i .NET 5.0, te analizatory są dołączone do [zestawu SDK platformy .NET.](/dotnet/fundamentals/code-analysis/overview) Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Aby uzyskać więcej informacji, zobacz [Migrowanie z analizatorów FxCop do analizatorów .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Konfigurowanie

Aby dowiedzieć się więcej na temat konfigurowania analizatorów .NET:

- Aby skonfigurować analizatory .NET, zobacz [Konfigurowanie analizatorów .NET.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

- Aby dowiedzieć się więcej o konfigurowaniu analizatorów przy użyciu wstępnie zdefiniowanych reguł za pomocą pliku EditorConfig lub pliku zestawu reguł, zobacz [Włączanie kategorii reguł.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

## <a name="see-also"></a>Zobacz też

- [Przechodzenie z analizatorów FxCop na analizatory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
