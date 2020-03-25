---
title: Migrowanie ze starszej wersji analizy (FxCop) do analizy źródłowej (analizatory FxCop)
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
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937582"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrowanie ze starszej wersji analizy (FxCop) do analizy źródłowej (analizatory FxCop)

Analiza źródła według .NET Compiler Platform ("Roslyn") analizatory zamieniają [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. W przypadku nowszych szablonów projektów, takich jak .NET Core i projekty .NET Standard, Starsza analiza nie jest dostępna.

Wiele reguł starszej analizy (FxCop) zostało już ponownie napisano dla analizatorów FxCop, zestaw Roslyn analizatorów kodu. Należy [zainstalować analizatory FxCop jako pakiet NuGet](install-fxcop-analyzers.md#nuget-package) , do którego odwołuje się projekt lub rozwiązanie. Analizatory FxCop uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

Aby uzyskać więcej informacji na temat różnic między starszą analizą i analizą źródła, zobacz następujące tematy:

- [Analiza kodu źródłowego w porównaniu do starszej analizy](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [Często zadawane pytania dotyczące analizatorów FxCop](../code-quality/fxcop-analyzers-faq.md)

Aby przeprowadzić migrację do analizy źródłowej, [Zainstaluj analizatory FxCop](../code-quality/install-fxcop-analyzers.md). Podobnie jak w przypadku starszych naruszeń reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie Lista błędów w programie Visual Studio. Ponadto naruszenia analizy kodu *źródłowego są również* wyświetlane w edytorze kodu jako zygzaky w kodzie błędu. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Aby wyświetlić stan reguł do nowych analizatorów FxCop, zobacz [porty i reguły nieportowe](../code-quality/fxcop-rule-port-status.md).

Aby dowiedzieć się więcej o konfigurowaniu analizatorów FxCop:

- Aby skonfigurować analizatory FxCop, zobacz [Konfigurowanie analizatorów FxCop](../code-quality/configure-fxcop-analyzers.md).

- Aby dowiedzieć się więcej o konfigurowaniu analizatorów przy użyciu wstępnie zdefiniowanych reguł z EditorConfig lub pliku zestawu reguł, zobacz [Włączanie kategorii reguł](../code-quality/analyzer-rule-sets.md).