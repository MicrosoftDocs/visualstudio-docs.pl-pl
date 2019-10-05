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
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974696"
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

Po [zainstalowaniu pakietu analizatora NuGet](install-roslyn-analyzers.md)Znajdź wstępnie zdefiniowany zestaw reguł w jego katalogu *zestawów reguł* . Jeśli na przykład przywoływano pakiet analizatora `Microsoft.CodeAnalysis.FxCopAnalyzers`, można znaleźć jego katalog *reguł* w lokalizacji *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*. Z tego miejsca Skopiuj jeden lub więcej zestawów reguł i wklej je w katalogu zawierającym projekt programu Visual Studio lub bezpośrednio do **Eksplorator rozwiązań**.

Możesz również [dostosować wstępnie zdefiniowany zestaw reguł](how-to-create-a-custom-rule-set.md) do preferencji. Na przykład można zmienić ważność jednej lub kilku reguł, aby naruszenia były wyświetlane jako błędy lub ostrzeżenia w **Lista błędów**.

## <a name="set-the-active-rule-set"></a>Ustaw aktywny zestaw reguł

Proces ustawiania aktywnego zestawu reguł jest nieco inny w zależności od tego, czy masz projekt .NET Core/. NET Standard lub projekt .NET Framework.

### <a name="net-core"></a>.NET Core

Aby ustawić regułę zestawu aktywnych reguł dla analizy w projektach .NET Core lub .NET Standard, ręcznie Dodaj właściwość **CodeAnalysisRuleSet** do pliku projektu. Na przykład poniższy fragment kodu ustawia `HelloWorld.ruleset` jako aktywny zestaw reguł.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Aby ustawić regułę zestawu aktywnych reguł dla analizy w .NET Framework projekty:

- Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.

- Na stronie właściwości projektu wybierz kartę **Analiza kodu** .

::: moniker range="vs-2017"

- W obszarze **Uruchom ten zestaw reguł**wybierz pozycję **Przeglądaj**, a następnie wybierz żądany zestaw reguł skopiowany do katalogu projektu.

::: moniker-end

::: moniker range=">=vs-2019"

- W obszarze **aktywne reguły**wybierz pozycję **Przeglądaj**, a następnie wybierz żądany zestaw reguł skopiowany do katalogu projektu.

::: moniker-end

   Teraz widzisz tylko naruszenia reguły dla tych reguł, które są włączone w wybranym zestawie reguł.

## <a name="available-rule-sets"></a>Dostępne zestawy reguł

Wstępnie zdefiniowane zestawy reguł analizatora obejmują trzy zestaw reguł, które mają wpływ na wszystkie reguły w pakiecie @ no__t-0one, które umożliwiają ich wszystkie, te, które wyłączają je wszystkie, i te, które są zgodne z domyślną ważnością i ustawieniami włączania każdej reguły:

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
