---
title: Migrowanie z FxCop do analizy źródłowej (analizatory FxCop)
ms.custom: SEO-VS-2020
description: Dowiedz się, jak analizować kod po raz pierwszy lub jak migrować z analizy binarnej (FxCop) do nowego sposobu analizowania kodu zarządzanego przy użyciu analizy źródłowej (analizatory FxCop).
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
ms.openlocfilehash: 9ce3c8feb3d3bbd458c14ee702d6e8a1668078f3
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658480"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrowanie ze starszej wersji analizy (FxCop) do analizy źródłowej (analizatory FxCop)

Analiza źródła według .NET Compiler Platform ("Roslyn") analizatory zamieniają [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. W przypadku nowszych szablonów projektów, takich jak .NET Core i projekty .NET Standard, Starsza analiza nie jest dostępna.

Wiele reguł starszej analizy (FxCop) zostało już ponownie napisano dla analizatorów FxCop, zestaw Roslyn analizatorów kodu. Należy [zainstalować analizatory FxCop jako pakiet NuGet](install-fxcop-analyzers.md#nuget-package) , do którego odwołuje się projekt lub rozwiązanie. Analizatory FxCop uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

Aby uzyskać więcej informacji na temat różnic między starszą analizą i analizą źródła, zobacz następujące tematy:

- [Analiza kodu źródłowego w porównaniu do starszej analizy](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [Często zadawane pytania dotyczące analizatorów FxCop](../code-quality/fxcop-analyzers-faq.md)

Aby przeprowadzić migrację do analizy źródłowej, [Zainstaluj analizatory FxCop](../code-quality/install-fxcop-analyzers.md). Podobnie jak w przypadku starszych naruszeń reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie Lista błędów w programie Visual Studio. Ponadto naruszenia analizy kodu *źródłowego są również* wyświetlane w edytorze kodu jako zygzaky w kodzie błędu. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) reguły. Aby wyświetlić stan reguł do nowych analizatorów FxCop, zobacz [porty i reguły nieportowe](../code-quality/fxcop-rule-port-status.md).

Aby dowiedzieć się więcej o konfigurowaniu analizatorów FxCop:

- Aby skonfigurować analizatory FxCop, zobacz [Konfigurowanie analizatorów FxCop](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Aby dowiedzieć się więcej o konfigurowaniu analizatorów przy użyciu wstępnie zdefiniowanych reguł z EditorConfig lub pliku zestawu reguł, zobacz [Włączanie kategorii reguł](/dotnet/fundamentals/code-analysis/code-quality-rule-options).