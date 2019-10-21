---
title: Zestawy reguł analizy kodu
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3bcce1b923b7c34ab5b163938999c0fdaeca649
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649038"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Korzystanie z zestawów reguł do grupowania reguł analizy kodu

Podczas konfigurowania analizy kodu w programie Visual Studio można wybrać jedną z listy wbudowanych *zestawów reguł*. Zestaw reguł jest grupą reguł analizy kodu, które identyfikują problemy skierowane i określone warunki dla tego projektu. Na przykład można zastosować zestaw reguł przeznaczony do skanowania kodu dla publicznie dostępnych interfejsów API. Można również zastosować zestaw reguł, który zawiera wszystkie dostępne reguły.

Zestaw reguł można dostosować, dodając lub usuwając reguły lub zmieniając jego wystąpienia tak, aby były wyświetlane jako ostrzeżenia lub błędy w **Lista błędów**. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Po dostosowaniu zestawu reguł Edytor zestawu reguł zawiera narzędzia do wyszukiwania i filtrowania, które ułatwiają proces.

Zestawy reguł są dostępne dla [analizy kodu zarządzanego](analyzer-rule-sets.md), [starszej analizy kodu zarządzanego](how-to-configure-code-analysis-for-a-managed-code-project.md)i [ C++ analizy kodu](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

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

## <a name="see-also"></a>Zobacz także

- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)
