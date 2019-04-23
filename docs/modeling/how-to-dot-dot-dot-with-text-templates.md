---
title: How to ... with — Szablony tekstowe
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89436ba28cd47463709fca9b7d6293dab934b549
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095935"
---
# <a name="how-to--with-text-templates"></a>How to ... with — Szablony tekstowe
Szablony tekstu w programie Visual Studio zapewniają wygodny sposób generowania tekstu dowolnego rodzaju. Aby wygenerować tekst w czasie wykonywania w ramach Twojej aplikacji i w czasie projektowania, aby wygenerować niektóre z kodu projektu, można użyć szablonów tekstowych. Ten temat zawiera podsumowanie najczęściej zadawane "Jak mogę...?" pytania.

 W tym temacie wielu odpowiedzi, które są poprzedzone punktory są sugestii alternatywnej.

 Aby uzyskać ogólne wprowadzenie do szablonów tekstowych, przeczytaj [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Jak...

### <a name="generate-part-of-my-application-code"></a>Generowanie część mojego kodu aplikacji
 Czy mogę mieć konfigurację lub *modelu* w pliku lub bazy danych. Co najmniej jeden części mój kod, zależą od tego modelu.

- Wygenerować niektóre z plików kodu z poziomu szablonów tekstu. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) i [co to jest najlepszym sposobem, aby rozpocząć pisanie szablonu?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generowanie plików w czasie wykonywania, przekazując dane do szablonu
 W czasie wykonywania Moja aplikacja generuje pliki tekstowe, takie jak raporty, zawierające kombinację standardowych tekstu i danych. Chcę, aby unikać pisania setki `write` instrukcji.

- Dodaj szablon tekstowy środowiska uruchomieniowego do projektu. Ten szablon utworzy klasę w kodzie, który można utworzyć wystąpienia i służy do generowania tekstu. Dane można przekazać do niego parametry konstruktora. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Jeśli chcesz wygenerować na podstawie szablonów, które są dostępne tylko w czasie wykonywania, można użyć szablonów tekstu standardowego. Jeśli piszesz rozszerzenie programu Visual Studio, można wywołać usługi szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). W innych kontekstach można użyć aparatu tworzenia szablonów tekstu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Użyj \<#@parameter#> dyrektywy w celu przekazania parametrów do tych szablonów. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca parametru](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Przeczytaj innego pliku projektu z szablonu
 Do odczytu pliku z tego samego projektu programu Visual Studio jako szablonu:

- Wstaw `hostSpecific="true"` do `<#@template#>` dyrektywy.

     W kodzie, należy użyć `this.Host.ResolvePath(filename)` uzyskać pełną ścieżkę pliku.

### <a name="invoke-methods-from-a-template"></a>Wywoływanie metod na podstawie szablonu
 Jeśli metody już istnieje, na przykład w standardzie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] klasy:

- Użyj \<#@assembly#> dyrektywy do załadowania zestawu oraz użyć \<#@import#> można ustawić kontekstu przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca importowania](../modeling/t4-import-directive.md).

   Jeśli często ten sam zestaw zestawów i dyrektywy import, należy wziąć pod uwagę pisania procesora dyrektywy. W każdym szablonie można wywoływać procesor dyrektywy, którego można załadować zestawów i plików modelu i Ustaw kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów T4 dotyczącej tekstu szablonu dyrektywy](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Jeśli piszesz metody samodzielnie:

- Jeśli piszesz szablonie tekstowym czasu wykonywania pisania definicji klasy częściowej, który ma taką samą nazwę jak szablon tekstowy środowiska uruchomieniowego. Dodaj dodatkowe metody do tej klasy.

- Blok sterowania cechami klasy zapisu `<#+ ... #>` , w którym można zadeklarować metody, właściwości i klasy prywatnej. Szablon tekstowy jest kompilowany, jest on przekształcany do klasy. Standardowe bloki sterujące `<#...#>` tekstu są przekształcane do pojedynczej metody i bloki cech klas są wstawiane jako elementy członkowskie w oddzielne. Aby uzyskać więcej informacji, zobacz [bloki formantów szablonów tekstowych](../modeling/text-template-control-blocks.md).

   Metody zdefiniowane jako funkcje klasy może również zawierać bloki tekstu osadzonych.

   Zaleca się umieszczenie funkcje klasy w oddzielnym pliku, który można `<#@include#>` do jednego lub więcej plików szablonu.

- Pisanie metod w osobnym zestawie (Biblioteka klas) i wywoływać je z szablonu. Użyj `<#@assembly#>` dyrektywy można załadować zestawu, a `<#@import#>` do ustawienia kontekstu przestrzeni nazw. Należy pamiętać, że aby odbudować zestawu podczas jej debugowania, może być konieczne zatrzymać i ponownie uruchomić program Visual Studio. Aby uzyskać więcej informacji, zobacz [dyrektywy T4 dotyczące szablonu tekstowego](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generowanie wielu plików z jednego modelu schematu
 Jeśli często Generuj pliki z modeli, które mają ten sam schemat XML lub baza danych:

- Należy wziąć pod uwagę, zapisywanie procesora dyrektywy. Dzięki temu można zastąpić użycie wielu instrukcji zestawu i zaimportuj instrukcje w każdy szablon przy użyciu pojedynczej dyrektywy niestandardowej. Procesor dyrektywy można załadować i przeanalizować pliku modelu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów T4 dotyczącej tekstu szablonu dyrektywy](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generowanie plików z modelu złożonego

- Rozważ tworzenie języka specyficznego dla domeny (DSL), do reprezentowania modelu. To ułatwia znacznie można zapisać szablonów, ponieważ używają typów i właściwości, które odzwierciedlają nazwy elementów w modelu. Nie masz przeanalizować pliku lub przechodzić węzłów XML. Na przykład:

     `foreach (Book book in this.Library) { ... }`

     Aby uzyskać więcej informacji, zobacz [wprowadzenie do języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md) i [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Pobieranie danych z programu Visual Studio
 Do korzystania z usług zawartym w programie Visual Studio, zestaw `hostSpecific` atrybut i obciążenia `EnvDTE` zestawu. Na przykład:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Wykonaj szablonów tekstowych w procesie kompilacji

- Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Bardziej ogólne pytania

### <a name="starting"></a> Co to jest najlepszym sposobem, aby rozpocząć pisanie szablonu tekstu?

1. Napisz szczegółowy przykład wygenerowany plik.

2. Włącz ją do szablonu tekstu, wstawiając `<#@template #>` dyrektywy oraz dyrektywy i kodu, które są wymagane do załadowania pliku wejściowego lub modelu.

3. Stopniowo Zamień części pliku wyrażenie i bloków kodu.

### <a name="what-is-a-model"></a>Co to jest "model"?

- Dane wejściowe odczytane przez szablon. Może to być w pliku lub w bazie danych. Może być, XML, lub rysunku programu Visio lub języka specyficznego dla domeny (DSL) lub modelu UML lub może to być zwykły tekst. Może on być rozkładane na kilka plików. Zazwyczaj więcej niż jeden szablon odczytuje jeden model.

     Implikacje "model" jest reprezentuje pewien aspekt firmie więcej bezpośrednio od kodu wygenerowanego programu lub innych plików. Na przykład jego może reprezentować plan sieci komunikacji, które supervise zostanie wygenerowany oprogramowania.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Co to jest zaleta użycia szablonów tekstu?
 Zwykle możesz wygenerować wiele kodu lub innych plików z jednego modelu. Model reprezentuje wymagania więcej bezpośrednio od wygenerowanego kodu. Go pominięto szczegóły implementacji i są zapisywane pod względem wymagań, a nie kod. Gdy zmienią się wymagania — jak zwykle — można zaktualizować modelu, łatwiejsze i bardziej niezawodne niż różnych części kodu programu.

 Generowanie kodu w związku z tym jest przydatnym narzędziem z punktu widzenia programowanie metodą agile metody.

### <a name="what-best-practices-are-there-for-text-templates"></a>Jakie "Najważniejsze wskazówki" są dostępne dla szablonów tekstowych?

- Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące szablonów tekstowych T4 pisania](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Co to jest "T4"?

- Inną nazwę dla programu Visual Studio możliwości szablonu tekstu, opisane w tym miejscu. Poprzedniej wersji, który nie został opublikowany, był skrót od "Przekształcenia szablonu tekstu".
