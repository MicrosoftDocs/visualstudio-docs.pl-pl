---
title: Zestawy reguł analizy kodu
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95b442835289265d197b6806c6d87fa051f2c1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825087"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Używanie zestawów reguł do grupowania reguł analizy kodu

Podczas konfigurowania analizy kodu w programie Visual Studio, możesz korzystać z listy wbudowanych *zestawów reguł*. Zestaw reguł jest grupowania reguł analizy kodu, które identyfikują docelowe problemy i określone warunki dla tego projektu. Na przykład można zastosować zestaw reguł, który jest przeznaczony do skanowania kodu w poszukiwaniu publicznie dostępnych interfejsów. Można także zastosować zestaw reguł, który zawiera wszystkie dostępne reguły.

Można dostosować reguły ustawiona przez dodanie lub usunięcie reguł lub zmieniając reguły ważności do wyświetlania jako ostrzeżenia lub błędy w **lista błędów**. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Po dostosowaniu zestawu reguł z edytora zestawu reguł dostarcza wyszukiwania i filtrowania narzędzia pomocne w procesie.

Zestawy reguł są dostępne dla [statycznej analizy kodu zarządzanego](how-to-configure-code-analysis-for-a-managed-code-project.md), [analizy kodu w języku C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md), i [analizatorów Roslyn](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Format zestawu reguł

Zestaw reguł jest określona w formacie XML w *.ruleset* pliku. Reguły, które składają się z Identyfikatora i *akcji*, są pogrupowane według Identyfikatora analizator i przestrzeni nazw w pliku.

Zawartość *.ruleset* pliku wygląda podobnie do tego kodu XML:

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
> Ułatwia to [Edytuj zestaw reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md) w graficznym **Edytor zestawu reguł** niż ręcznie.

## <a name="specify-a-rule-set-for-a-project"></a>Określ zestaw reguł dla projektu

Zestaw dla projektu określono za pomocą reguł **CodeAnalysisRuleSet** właściwość w pliku projektu programu Visual Studio. Na przykład:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz także

- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)