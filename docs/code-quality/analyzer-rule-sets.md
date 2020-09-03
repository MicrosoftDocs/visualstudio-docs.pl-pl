---
title: Zestawy reguł analizatora FxCop i pliki editorconfig
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b99bb08c82725f19f7985a97656edf65f112d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800219"
---
# <a name="enable-a-category-of-rules"></a>Włączanie kategorii reguł

Pakiety analizatora mogą zawierać wstępnie zdefiniowane pliki [EditorConfig](use-roslyn-analyzers.md#rule-severity) i [zestawów reguł](using-rule-sets-to-group-code-analysis-rules.md) , które ułatwiają szybkie i łatwe Włączanie kategorii reguł, takich jak zabezpieczenia czy reguły projektowania. Pakiet analizatora NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) zawiera oba zestawy reguł (począwszy od wersji 2.6.2) i pliki EditorConfig (począwszy od wersji 2.9.5). Przez włączenie określonej kategorii reguł można zidentyfikować odpowiednie problemy i określone warunki.

> [!NOTE]
> Włączanie reguł analizatora i Ustawianie ich ważności przy użyciu pliku EditorConfig jest obsługiwane w programie Visual Studio 2019 w wersji 16,3.

Pakiet NuGet analizatora FxCop zawiera wstępnie zdefiniowane zestawy reguł i pliki EditorConfig dla następujących kategorii reguł:

- Wszystkie reguły
- Przepływ danych
- Projekt
- Dokumentacja
- Globalizacja
- Współdziałanie
- Łatwość konserwacji
- Nazewnictwo
- Wydajność
- Przewoźny z FxCop
- Niezawodność
- Bezpieczeństwo
- Użycie

Każda z tych kategorii reguł ma plik EditorConfig lub zestawu reguł, aby:

- Włącz wszystkie reguły w kategorii (i Wyłącz wszystkie inne reguły)
- Użyj domyślnej ważności i ustawienia włączania każdej reguły (i Wyłącz wszystkie inne reguły)

> [!TIP]
> Kategoria "wszystkie reguły" ma dodatkowy plik EditorConfig lub zestawu reguł, aby wyłączyć wszystkie reguły. Użyj tego pliku, aby szybko pozbyć się wszelkich ostrzeżeń lub błędów analizatora w projekcie.

> [!TIP]
> Jeśli migrujesz ze starszej analizy "FxCop" do analizy kodu opartej na .NET Compiler Platform, pliki EditorConfig i zestawu reguł umożliwiają kontynuowanie korzystania z konfiguracji podobnej reguły do [tych, które zostały wcześniej użyte](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Wstępnie zdefiniowane pliki EditorConfig

Wstępnie zdefiniowane pliki EditorConfig pakietu Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer znajdują się w katalogu *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig* . Na przykład plik EditorConfig, aby włączyć wszystkie reguły zabezpieczeń, znajduje się w lokalizacji *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Skopiuj wybrany plik editorconfig do katalogu głównego projektu.

## <a name="predefined-rule-sets"></a>Zestawy wstępnie zdefiniowanych reguł

Wstępnie zdefiniowane pliki zestawu reguł dla pakietu Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer znajdują się w katalogu *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets* . Na przykład plik zestawu reguł, aby włączyć wszystkie reguły zabezpieczeń, znajduje się w lokalizacji *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.RuleSet*.

Skopiuj co najmniej jeden zestaw reguł i wklej je w katalogu zawierającym projekt programu Visual Studio lub bezpośrednio do **Eksplorator rozwiązań**.

Możesz również [dostosować wstępnie zdefiniowany zestaw reguł](how-to-create-a-custom-rule-set.md) do preferencji. Na przykład można zmienić ważność jednej lub kilku reguł, aby naruszenia były wyświetlane jako błędy lub ostrzeżenia w **Lista błędów**.

### <a name="set-the-active-rule-set"></a>Ustaw aktywny zestaw reguł

Proces ustawiania aktywnego zestawu reguł jest nieco inny w zależności od tego, czy masz projekt .NET Core/. NET Standard lub projekt .NET Framework.

#### <a name="net-core"></a>.NET Core

Aby ustawić regułę zestawu aktywnych reguł dla analizy w projektach .NET Core lub .NET Standard, ręcznie Dodaj właściwość **CodeAnalysisRuleSet** do pliku projektu. Na przykład poniższy fragment kodu jest ustawiany `HelloWorld.ruleset` jako aktywny zestaw reguł.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>Zobacz też

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Omówienie analizatorów .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Zainstaluj analizatory](install-roslyn-analyzers.md)
- [Konfiguruj analizatory](use-roslyn-analyzers.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md)
