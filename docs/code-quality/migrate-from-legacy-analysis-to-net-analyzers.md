---
title: Migrowanie z FxCop do analizy źródłowej (analizatory .NET)
ms.custom: SEO-VS-2020
description: Dowiedz się, jak analizować kod po raz pierwszy lub jak przeprowadzić migrację z analizy binarnej (FxCop) do nowego sposobu analizowania kodu zarządzanego przy użyciu analizy źródłowej (analizatory .NET).
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
ms.openlocfilehash: 96a0c0b7fa1f2c703cefde31070ed98c5edddcb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859765"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrowanie ze starszej wersji analizy (FxCop) do analizy źródłowej (analizatory .NET)

Analiza źródła według .NET Compiler Platform ("Roslyn") analizatory zamieniają [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. W przypadku nowszych szablonów projektów, takich jak .NET Core i projekty .NET Standard, Starsza analiza nie jest dostępna.

Wiele reguł starszej analizy (FxCop) zostało już ponownie napisano dla analizatorów .NET, zestawu Roslyn analizatorów kodu. Analizatory Roslyn uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

Aby uzyskać więcej informacji na temat różnic między starszą analizą i analizą źródła, zobacz następujące tematy:

- [Analiza kodu źródłowego w porównaniu do starszej analizy](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

- [Często zadawane pytania dotyczące analizatorów .NET](../code-quality/net-analyzers-faq.md)

## <a name="migration"></a>Migracja

Aby przeprowadzić migrację do analizy źródłowej, [Włącz lub zainstaluj analizatory .NET](install-net-analyzers.md). Podobnie jak w przypadku starszych naruszeń reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie Lista błędów w programie Visual Studio. Ponadto naruszenia analizy kodu *źródłowego są również* wyświetlane w edytorze kodu jako zygzaky w kodzie błędu. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) reguły. Aby wyświetlić stan reguł portów do nowych analizatorów .NET, zobacz [port i reguły nieportowe](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> W systemach starszych niż Visual Studio 2019 16,8 i .NET 5,0 te analizatory są dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Aby uzyskać więcej informacji, zobacz [Migrowanie z analizatorów FxCop do analizatorów .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Konfigurowanie

Aby dowiedzieć się więcej o konfigurowaniu analizatorów .NET:

- Aby skonfigurować analizatory .NET, zobacz [Configure .NET analizators](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Aby dowiedzieć się więcej o konfigurowaniu analizatorów przy użyciu wstępnie zdefiniowanych reguł z EditorConfig lub pliku zestawu reguł, zobacz [Włączanie kategorii reguł](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Zobacz też

- [Przechodzenie z analizatorów FxCop na analizatory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
