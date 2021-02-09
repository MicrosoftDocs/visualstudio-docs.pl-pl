---
title: Zestawy reguł analizy kodu
ms.date: 04/02/2018
description: Dowiedz się więcej na temat wbudowanych i niestandardowych zestawów reguł w programie Visual Studio Code Analysis. Zobacz jak określić zestawy reguł w plikach i jak skonfigurować zestawy reguł w projektach.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 980c77067ac237dba13c8c888c358a0adeab6d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859661"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Korzystanie z zestawów reguł do grupowania reguł analizy kodu

Podczas konfigurowania analizy kodu w programie Visual Studio można wybrać jedną z listy wbudowanych *zestawów reguł*. Zestaw reguł jest grupą reguł analizy kodu, które identyfikują problemy skierowane i określone warunki dla tego projektu. Na przykład można zastosować zestaw reguł przeznaczony do skanowania kodu dla publicznie dostępnych interfejsów API. Można również zastosować zestaw reguł, który zawiera wszystkie dostępne reguły.

Zestaw reguł można dostosować, dodając lub usuwając reguły lub zmieniając jego wystąpienia tak, aby były wyświetlane jako ostrzeżenia lub błędy w **Lista błędów**. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Po dostosowaniu zestawu reguł Edytor zestawu reguł zawiera narzędzia do wyszukiwania i filtrowania, które ułatwiają proces.

Zestawy reguł są dostępne na potrzeby [analizy kodu zarządzanego](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [starszej analizy kodu zarządzanego](how-to-configure-code-analysis-for-a-managed-code-project.md)i [analizy kodu w języku C++](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Format zestawu reguł

Zestaw reguł jest określony w formacie XML w pliku zestawu *reguł* . Reguły, które składają się z identyfikatora i *akcji*, są pogrupowane według identyfikatora analizatora i przestrzeni nazw w pliku.

Zawartość pliku. zestawu *reguł* wygląda podobnie do tego kodu XML:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Łatwiej jest [edytować zestaw reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md) w **edytorze zestawu reguł** graficznych niż ręcznie.

## <a name="specify-a-rule-set-for-a-project"></a>Określanie zestawu reguł dla projektu

Zestaw reguł dla projektu jest określany przez właściwość **CodeAnalysisRuleSet** w pliku projektu programu Visual Studio. Na przykład:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie zestawu reguł analizy kodu](../code-quality/rule-set-reference.md)