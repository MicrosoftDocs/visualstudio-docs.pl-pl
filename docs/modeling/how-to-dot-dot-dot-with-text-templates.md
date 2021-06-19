---
title: How to ... with — Szablony tekstowe
description: Dowiedz się więcej na temat odpowiedzi na często zadawane pytania, które wystąpiły podczas używania szablonów tekstowych do generowania tekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c65a7ba67c3972620b3d589188e233827a12ffd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387271"
---
# <a name="how-to--with-text-templates"></a>How to ... with — Szablony tekstowe
Szablony tekstowe w Visual Studio zapewniają przydatny sposób generowania tekstu dowolnego rodzaju. Za pomocą szablonów tekstowych można generować tekst w czasie rzeczywistym w ramach aplikacji, a w czasie projektowania wygenerować część kodu projektu. Ten temat zawiera podsumowanie najczęściej zadawanych Jak mogę ...?" Pytania.

 W tym temacie wiele odpowiedzi, które są poprzedzone punktorami, to sugestie alternatywne.

 Ogólne wprowadzenie do szablonów tekstowych można znaleźć w [tematach Generowanie kodu i Szablony tekstowe T4.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="how-to-"></a>Jak...

### <a name="generate-part-of-my-application-code"></a>Generowanie części kodu aplikacji
 Mam konfigurację lub *model w* pliku lub bazie danych. Co najmniej jedna część kodu zależy od tego modelu.

- Wygeneruj niektóre pliki kodu na podstawie szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md) (Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4) i What is the best way to start writing a template? (Jaki jest najlepszy sposób na [rozpoczęcie pisania szablonu?).](#starting)

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generowanie plików w czasie uruchamiania, przekazywanie danych do szablonu
 W czasie działania moja aplikacja generuje pliki tekstowe, takie jak raporty, które zawierają połączenie standardowego tekstu i danych. Chcę uniknąć pisania setek `write` instrukcji.

- Dodaj szablon tekstowy środowiska uruchomieniowego do projektu. Ten szablon tworzy klasę w kodzie, która umożliwia utworzenie wystąpienia i użycie go do wygenerowania tekstu. Dane można przekazać do niego w parametrach konstruktora. Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

- Jeśli chcesz generować na podstawie szablonów, które są dostępne tylko w czasie uruchamiania, możesz użyć standardowych szablonów tekstowych. Jeśli piszesz rozszerzenie Visual Studio, możesz wywołać usługę szablonów tekstu. Aby uzyskać więcej informacji, zobacz [Temat Invoking Text Transformation in a VS Extension (Wywołania przekształcenia tekstu w rozszerzeniu programu VS).](../modeling/invoking-text-transformation-in-a-vs-extension.md) W innych kontekstach można użyć aparatu szablonów tekstu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Użyj dyrektywy \<#@parameter#> , aby przekazać parametry do tych szablonów. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 parameter .](../modeling/t4-parameter-directive.md)

### <a name="read-another-project-file-from-a-template"></a>Odczytywanie innego pliku projektu z szablonu
 Aby odczytać plik z tego samego Visual Studio projektu jako szablonu:

- Wstaw `hostSpecific="true"` do `<#@template#>` dyrektywy .

     W kodzie użyj , aby uzyskać pełną `this.Host.ResolvePath(filename)` ścieżkę pliku.

### <a name="invoke-methods-from-a-template"></a>Wywoływanie metod z szablonu

Jeśli metody już istnieją, na przykład w klasach .NET:

- Użyj dyrektywy \<#@assembly#> , aby załadować zestaw, a następnie użyj \<#@import#> elementu , aby ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 import](../modeling/t4-import-directive.md).

   Jeśli często używasz tego samego zestawu dyrektyw zestawu i importu, rozważ napisanie procesora dyrektywy. W każdym szablonie można wywołać procesor dyrektywy, który może załadować zestawy i pliki modelu oraz ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz Creating Custom T4 Text Template Directive Processors (Tworzenie niestandardowych procesorów [dyrektyw szablonów tekstowych T4).](../modeling/creating-custom-t4-text-template-directive-processors.md)

Jeśli piszesz metody samodzielnie:

- Jeśli piszesz szablon tekstowy środowiska uruchomieniowego, napisz częściową definicję klasy o takiej samej nazwie jak szablon tekstowy środowiska uruchomieniowego. Dodaj dodatkowe metody do tej klasy.

- Napisz blok sterowania cechami `<#+ ... #>` klas, w którym można deklarować metody, właściwości i klasy prywatne. Podczas kompilowania szablonu tekstowego jest on przekształcany w klasę. Standardowe bloki sterujące i tekst są przekształcane w jedną metodę, a bloki cech klas są wstawiane `<#...#>` jako oddzielne składowe. Aby uzyskać więcej informacji, zobacz [Bloki kontrolek szablonu tekstu](../modeling/text-template-control-blocks.md).

   Metody zdefiniowane jako cechy klasy mogą również zawierać osadzone bloki tekstowe.

   Rozważ umieszczenie cech klasy w oddzielnym pliku, który można `<#@include#>` umieszczać w co najmniej jednym pliku szablonu.

- Napisz metody w osobnym zestawie (bibliotece klas) i wywołaj je z szablonu. Użyj dyrektywy `<#@assembly#>` , aby załadować zestaw i `<#@import#>` , aby ustawić kontekst przestrzeni nazw. Należy pamiętać, że w celu ponownego skompilowania zestawu podczas debugowania może być konieczne zatrzymanie i ponowne uruchomienie Visual Studio. Aby uzyskać więcej informacji, zobacz [dyrektywy T4 dotyczące szablonów tekstowych](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generowanie wielu plików na podstawie jednego schematu modelu
 Jeśli często generujesz pliki z modeli, które mają ten sam schemat XML lub bazy danych:

- Rozważ napisanie procesora dyrektywy. Dzięki temu można zastąpić wiele instrukcji zestawu i importować instrukcje w każdym szablonie pojedynczą niestandardową dyrektywą. Procesor dyrektywy może również załadować i analizuje plik modelu. Aby uzyskać więcej informacji, zobacz Creating Custom T4 Text Template Directive Processors (Tworzenie niestandardowych procesorów [dyrektyw szablonów tekstowych T4).](../modeling/creating-custom-t4-text-template-directive-processors.md)

### <a name="generate-files-from-a-complex-model"></a>Generowanie plików na podstawie złożonego modelu

- Rozważ utworzenie języka specyficznego dla domeny (DSL) reprezentującego model. Znacznie ułatwia to pisanie szablonów, ponieważ używasz typów i właściwości, które odzwierciedlają nazwy elementów w modelu. Nie trzeba analizowania pliku ani nawigowania po węzłach XML. Na przykład:

     `foreach (Book book in this.Library) { ... }`

     Aby uzyskać więcej informacji, zobacz Wprowadzenie with Domain-Specific Languages (Język [Domain-Specific)](../modeling/getting-started-with-domain-specific-languages.md) i Generating Code from a Domain-Specific Language (Generowanie kodu [z Domain-Specific języku).](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Pobierz dane z Visual Studio
 Aby użyć usług oferowanych w Visual Studio, ustaw `hostSpecific` atrybut i załaduj `EnvDTE` zestaw. Na przykład:

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

### <a name="execute-text-templates-in-the-build-process"></a>Wykonywanie szablonów tekstowych w procesie kompilacji

- Aby uzyskać więcej informacji, zobacz [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Bardziej ogólne pytania

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Jaki jest najlepszy sposób rozpoczęcia pisania szablonu tekstowego?

1. Napisz konkretny przykład wygenerowanego pliku.

2. Przekrój go w szablon tekstowy, wstawiając dyrektywę oraz dyrektywy i kod, które są wymagane do załadowania pliku `<#@template #>` lub modelu wejściowego.

3. Stopniowe zastępowanie części pliku blokami wyrażenia i kodu.

### <a name="what-is-a-model"></a>Co to jest "model"?

- Dane wejściowe odczytane przez szablon. Może on być w pliku lub w bazie danych. Może to być język XML, rysunek programu Visio, język specyficzny dla domeny (DSL) lub model UML albo zwykły tekst. Może on być rozłożony na kilka plików. Zazwyczaj więcej niż jeden szablon odczytuje jeden model.

     Implikacja terminu "model" jest taka, że reprezentuje ona pewien aspekt firmy bardziej bezpośrednio niż wygenerowany kod programu lub inne pliki. Na przykład może reprezentować plan sieci komunikacyjnej, która będzie nadzorowana przez wygenerowane oprogramowanie.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Jakie są korzyści z używania szablonów tekstowych?
 Zazwyczaj generujesz wiele kodu lub innych plików z jednego modelu. Model reprezentuje wymagania bardziej bezpośrednio niż wygenerowany kod. Pomija szczegóły implementacji i jest pisany w kategoriach wymagań, a nie kodu. Gdy wymagania zmieniają się — jak zwykle — można zaktualizować model łatwiej i bardziej niezawodnie niż różne części kodu programu.

 Generowanie kodu jest w związku z tym cennym narzędziem z perspektywy zwinnych metod pisania kodu.

### <a name="what-best-practices-are-there-for-text-templates"></a>Jakie "najlepsze rozwiązania" są dostępne dla szablonów tekstowych?

- Aby uzyskać więcej informacji, zobacz Guidelines for Writing T4 Text Templates (Wytyczne [dotyczące pisania szablonów tekstowych T4).](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>Co to jest "T4"?

- Inna nazwa możliwości szablonu Visual Studio opisanych tutaj. Poprzednia wersja, która nie została opublikowana, była skrótem "Przekształcenia szablonu tekstu".
