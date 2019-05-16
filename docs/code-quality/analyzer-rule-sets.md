---
title: Zestawy reguł analizatora
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696e6bd46c17054494be2ea0e0f2a1af4fd703d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675486"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Zestawy reguł na potrzeby analizatorów Roslyn

Zestawy wstępnie zdefiniowanych reguł są dołączane do niektórych pakietów analizatora NuGet. Na przykład zestawy reguł, które są dołączone [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pakiet analizatora NuGet (począwszy od wersji 2.6.2) Włącz lub Wyłącz zasady na podstawie ich kategorii, takie jak zabezpieczenia, nazw, lub wydajność. Korzystanie z zestawów reguł można łatwo szybko wyświetlić tylko te naruszenia reguły, które odnoszą się do określonej kategorii reguły.

W przypadku migrowania ze starszego "FxCop" statycznej analizy kodu do analizatorów Roslyn, te zestawy reguł umożliwiają kontynuowanie przy użyciu tej samej konfiguracji reguły, wcześniej używane.

## <a name="use-analyzer-rule-sets"></a>Korzystanie z zestawów reguł analizatora

Po zakończeniu [zainstaluj pakiet analizatora NuGet](install-roslyn-analyzers.md), zlokalizuj wstępnie zdefiniowany zestaw reguł jego *zestawów reguł* katalogu. Na przykład, jeśli odwołujesz `Microsoft.CodeAnalysis.FxCopAnalyzers` analizatora pakietów, możesz znaleźć jej *zestawów reguł* katalogu na *% USERPROFILE %\\.nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\ \<wersji\>\rulesets*. Stamtąd skopiować jednego lub więcej zestawów reguł, a następnie wklej je w katalogu, który zawiera projektu programu Visual Studio lub bezpośrednio do **Eksploratora rozwiązań**.

Możesz również [Dostosuj zestaw wstępnie zdefiniowanych reguł](how-to-create-a-custom-rule-set.md) zgodnie z preferencjami. Na przykład zmienić ważność co najmniej jedną regułę tak, aby naruszeń są traktowane jako błędy lub ostrzeżenia w **lista błędów**.

## <a name="set-the-active-rule-set"></a>Ustaw aktywny zestaw reguł

Proces ustawiania aktywny zestaw reguł jest nieco inne w zależności od tego, czy masz projekt .NET Core/.NET Standard lub projekt programu .NET Framework.

### <a name="net-core"></a>.NET Core

Aby utworzyć regułę ustawić aktywny zestaw reguł dla analizy w projektach .NET Core lub .NET Standard, należy ręcznie dodać **CodeAnalysisRuleSet** właściwość do pliku projektu. Na przykład, poniższy kod ustawia fragment `HelloWorld.ruleset` jako aktywna reguła zestawu.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Aby aktywny zestaw reguł dla analizy w projektach .NET Framework zestaw reguł, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. Na stronach właściwości projektu, wybierz **analizy kodu** kartę. W obszarze **Uruchom ten zestaw reguł**, wybierz opcję **Przeglądaj**, a następnie wybierz odpowiednią regułę zestaw, który został skopiowany do katalogu projektu. Teraz widoczne tylko naruszeń zasady dla tych reguł, które są włączone w wybranym zestawem reguł.

## <a name="available-rule-sets"></a>Zestawy reguł dostępne

Analizator wstępnie zdefiniowane zestawy reguł obejmują trzy zestawów reguł, które wpływają na wszystkie reguły w pakiecie&mdash;taki, który umożliwia ich wszystkich, taki, który wyłącza je wszystkie, a drugie honoruje każdej reguły domyślne ważności i włączenie ustawienia:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Ponadto istnieją dwa zestawy reguł dla każdej kategorii reguły w pakiecie, takich jak wydajność czy zabezpieczeń. Jeden zestaw reguł włącza wszystkie reguły dla kategorii, a jeden zestaw reguł honoruje ważność i włączenie wartości domyślne dla każdej reguły w kategorii.

[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pakiet analizatora NuGet obejmuje zestawy reguł w ramach następujących kategorii, które dopasowanie zestawów reguł na dostępne dla starszej wersji "FxCop" statycznej analizy kodu:

- projekt
- dokumentacja
- utrzymanie
- nazewnictwo
- wydajność
- niezawodność
- zabezpieczenia
- wykorzystanie

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Omówienie analizatory platformie kompilatora .NET](roslyn-analyzers-overview.md)
- [Instalowanie analizatorów](install-roslyn-analyzers.md)
- [Użyj analizatorów](use-roslyn-analyzers.md)
- [Używanie zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md)
