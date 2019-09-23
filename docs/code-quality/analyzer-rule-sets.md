---
title: Zestawy reguł analizatora FxCop
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1567dd088ecc060f031e59827ff33024e9e955
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185951"
---
# <a name="rule-sets-for-analyzer-packages"></a>Zestawy reguł dla pakietów analizatora

Wstępnie zdefiniowane zestawy reguł są zawarte w niektórych pakietach analizatora NuGet. Na przykład zestawy reguł, które są dołączone do pakietu analizatora NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (począwszy od wersji 2.6.2), włączają lub wyłączają reguły oparte na ich kategorii, takie jak zabezpieczenia, nazewnictwo lub wydajność. Używanie zestawów reguł ułatwia szybkie wyświetlanie tylko naruszeń reguł, które odnoszą się do określonej kategorii reguł.

Zestaw reguł jest grupą reguł analizy kodu, które identyfikują problemy skierowane i określone warunki. Zestawy reguł umożliwiają włączanie lub wyłączanie reguł oraz Ustawianie ważności naruszeń reguł. Pakiet NuGet analizatora FxCop zawiera wstępnie zdefiniowane zestawy reguł dla następujących kategorii reguł:

- projekt
- dokumentacja
- utrzymanie
- nazewnictwo
- wydajność
- niezawodność
- zabezpieczenia
- wykorzystanie

Jeśli migrujesz ze starszej analizy "FxCop" do analizy kodu na podstawie .NET Compiler Platform, te zestawy reguł umożliwiają kontynuowanie korzystania z podobnych konfiguracji reguł do [tych, które zostały wcześniej użyte](rule-set-reference.md).

## <a name="use-analyzer-package-rule-sets"></a>Użyj zestawów reguł pakietu analizatora

Po [zainstalowaniu pakietu analizatora NuGet](install-roslyn-analyzers.md)Znajdź wstępnie zdefiniowany zestaw reguł w jego katalogu *zestawów reguł* . Jeśli na `Microsoft.CodeAnalysis.FxCopAnalyzers` przykład przywoływano pakiet analizatora, można znaleźć jego katalog *reguł* w lokalizacji *% USERPROFILE%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\< \rulesets\>* . Z tego miejsca Skopiuj jeden lub więcej zestawów reguł i wklej je w katalogu zawierającym projekt programu Visual Studio lub bezpośrednio do **Eksplorator rozwiązań**.

Możesz również [dostosować wstępnie zdefiniowany zestaw reguł](how-to-create-a-custom-rule-set.md) do preferencji. Na przykład można zmienić ważność jednej lub kilku reguł, aby naruszenia były wyświetlane jako błędy lub ostrzeżenia w **Lista błędów**.

## <a name="set-the-active-rule-set"></a>Ustaw aktywny zestaw reguł

Proces ustawiania aktywnego zestawu reguł jest nieco inny w zależności od tego, czy masz projekt .NET Core/. NET Standard lub projekt .NET Framework.

### <a name="net-core"></a>.NET Core

Aby ustawić regułę zestawu aktywnych reguł dla analizy w projektach .NET Core lub .NET Standard, ręcznie Dodaj właściwość **CodeAnalysisRuleSet** do pliku projektu. Na przykład poniższy fragment kodu jest ustawiany `HelloWorld.ruleset` jako aktywny zestaw reguł.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Aby ustawić regułę zestawu aktywnych reguł dla analizy w .NET Framework projekty, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Na stronie właściwości projektu wybierz kartę **Analiza kodu** . W obszarze **Uruchom ten zestaw reguł**wybierz pozycję **Przeglądaj**, a następnie wybierz żądany zestaw reguł skopiowany do katalogu projektu. Teraz widzisz tylko naruszenia reguły dla tych reguł, które są włączone w wybranym zestawie reguł.

## <a name="available-rule-sets"></a>Dostępne zestawy reguł

Wstępnie zdefiniowane zestawy reguł analizatora obejmują trzy zestaw reguł, które mają wpływ na wszystkie reguły&mdash;w pakiecie, które włączają je wszystkie, ale te, które je wyłączyją, i są uznawane za wszystkie zasady ważności i ustawienia włączania każdej reguły:

- AllRulesEnabled. zestaw reguł
- AllRulesDisabled. zestaw reguł
- AllRulesDefault. zestaw reguł

Ponadto istnieją dwa zestawy reguł dla każdej kategorii reguł w pakiecie, takie jak wydajność lub zabezpieczenia. Jeden zestaw reguł włącza wszystkie reguły dla kategorii, a jeden zestaw reguł uwzględnia domyślne ważności i ustawienia włączania dla każdej reguły w kategorii.

Pakiet analizatora NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) zawiera zestawy reguł dla następujących kategorii:

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
- [Omówienie analizatorów .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Zainstaluj analizatory](install-roslyn-analyzers.md)
- [Konfiguruj analizatory](use-roslyn-analyzers.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md)
