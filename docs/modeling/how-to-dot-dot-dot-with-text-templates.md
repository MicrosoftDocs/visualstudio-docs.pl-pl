---
title: How to ... with — Szablony tekstowe
description: Poznaj odpowiedzi na często zadawane pytania dotyczące generowania tekstu przy użyciu szablonów tekstowych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50844ce8c6943fcf6b2a0b91c7fd2cfcb6184094
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363188"
---
# <a name="how-to--with-text-templates"></a>How to ... with — Szablony tekstowe
Szablony tekstowe w programie Visual Studio zapewniają przydatny sposób generowania tekstu dowolnego rodzaju. Za pomocą szablonów tekstowych można generować tekst w czasie wykonywania jako część aplikacji i w czasie projektowania, aby wygenerować część kodu projektu. W tym temacie przedstawiono podsumowanie najczęściej zaproszonych "Jak mogę...?" masz.

 W tym temacie wiele odpowiedzi, które są poprzedzone punktorami, są sugestiami alternatywnymi.

 Aby zapoznać się z ogólnym wprowadzeniem do szablonów tekstowych, przeczytaj temat [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Jak...

### <a name="generate-part-of-my-application-code"></a>Generuj część mojego kodu aplikacji
 Mam konfigurację lub *model* w pliku lub bazie danych. Co najmniej jedna część mojego kodu jest zależna od tego modelu.

- Generuj niektóre pliki kodu z szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) i [jaki jest najlepszy sposób rozpoczęcia pisania szablonu?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generowanie plików w czasie wykonywania, przekazywanie danych do szablonu
 W czasie wykonywania moja aplikacja generuje pliki tekstowe, takie jak raporty, które zawierają kombinację standardowego tekstu i danych. Chcę uniknąć pisania setek `write` instrukcji.

- Dodaj szablon tekstu środowiska uruchomieniowego do projektu. Ten szablon służy do tworzenia klasy w kodzie, którą można utworzyć i użyć do generowania tekstu. W parametrach konstruktora można przekazać do niego dane. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Jeśli chcesz generować z szablonów, które są dostępne tylko w czasie wykonywania, możesz użyć standardowych szablonów tekstowych. Jeśli piszesz rozszerzenie programu Visual Studio, możesz wywołać usługę Text tworzenia szablonów. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). W innych kontekstach można użyć aparatu tekstu tworzenia szablonów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Użyj \<#@parameter#> dyrektywy do przekazania parametrów do tych szablonów. Aby uzyskać więcej informacji, zobacz [dyrektywa parametrów T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Odczytaj inny plik projektu z szablonu
 Aby odczytać plik z tego samego projektu programu Visual Studio co szablon:

- Wstaw `hostSpecific="true"` do `<#@template#>` dyrektywy.

     W kodzie, użyj, `this.Host.ResolvePath(filename)` Aby uzyskać pełną ścieżkę pliku.

### <a name="invoke-methods-from-a-template"></a>Wywoływanie metod z szablonu

Jeśli istnieją już metody, na przykład w klasach .NET:

- Użyj \<#@assembly#> dyrektywy do załadowania zestawu i Użyj, \<#@import#> Aby ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dyrektywa importowania T4](../modeling/t4-import-directive.md).

   Jeśli często używasz tego samego zestawu dyrektyw Assembly i import, rozważ zapisanie procesora dyrektywy. W każdym szablonie można wywołać procesor dyrektywy, który może ładować zestawy i pliki modelu i ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

Jeśli piszesz metody samodzielnie:

- W przypadku pisania szablonu tekstu środowiska uruchomieniowego należy napisać częściową definicję klasy, która ma taką samą nazwę jak szablon tekstu środowiska uruchomieniowego. Dodaj dodatkowe metody do tej klasy.

- Napisz blok sterowania cechą klasy `<#+ ... #>` , w którym można zadeklarować metody, właściwości i klasy prywatne. Po skompilowaniu szablonu tekstu jest on przekształcany w klasę. Standardowe bloki kontrolne `<#...#>` i tekst są przekształcane na pojedynczą metodę, a bloki funkcji klasy są wstawiane jako odrębne elementy członkowskie. Aby uzyskać więcej informacji, zobacz [bloki kontrolne szablonu tekstu](../modeling/text-template-control-blocks.md).

   Metody zdefiniowane jako funkcje klasy mogą również zawierać osadzone bloki tekstu.

   Rozważ umieszczenie funkcji klasy w osobnym pliku, który można `<#@include#>` umieścić w jednym lub kilku plikach szablonów.

- Napisz metody w osobnym zestawie (bibliotece klas) i Wywołaj je z szablonu. Użyj `<#@assembly#>` dyrektywy do załadowania zestawu i `<#@import#>` Ustawienia kontekstu przestrzeni nazw. Należy pamiętać, że w celu odbudowania zestawu podczas jego debugowania może być konieczne zatrzymanie i ponowne uruchomienie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generowanie wielu plików z jednego schematu modelu
 Jeśli często generowane są pliki z modeli, które mają ten sam schemat XML lub bazy danych:

- Rozważ zapisanie procesora dyrektywy. Pozwala to na zamianę wielu instrukcji zestawu i instrukcji importu w każdym szablonie z pojedynczą dyrektywą niestandardową. Procesor dyrektywy może również ładować i analizować plik modelu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generowanie plików z modelu złożonego

- Rozważ utworzenie języka specyficznego dla domeny (DSL) do reprezentowania modelu. Dzięki temu można znacznie łatwiej pisać szablony, ponieważ używasz typów i właściwości, które odzwierciedlają nazwy elementów w modelu. Nie jest konieczne analizowanie pliku ani nawigowanie po węzłach XML. Na przykład:

     `foreach (Book book in this.Library) { ... }`

     Aby uzyskać więcej informacji, zobacz [wprowadzenie w językach Domain-Specific](../modeling/getting-started-with-domain-specific-languages.md) i [generowanie kodu z poziomu języka Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Pobieranie danych z programu Visual Studio
 Aby korzystać z usług oferowanych w programie Visual Studio, ustaw `hostSpecific` atrybut i Załaduj `EnvDTE` zestaw. Na przykład:

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

- Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Więcej pytań ogólnych

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Co to jest najlepszy sposób na rozpoczęcie pisania szablonu tekstu?

1. Napisz konkretny przykład wygenerowanego pliku.

2. Przekształcenie go w szablon tekstowy przez wstawienie `<#@template #>` dyrektywy i dyrektyw i kodu, które są wymagane do załadowania pliku wejściowego lub modelu.

3. Stopniowo zamieniaj części pliku na bloki wyrażeń i kodu.

### <a name="what-is-a-model"></a>Co to jest "model"?

- Dane wejściowe są odczytywane przez szablon. Może ona znajdować się w pliku lub w bazie danych. Może to być kod XML lub rysunek programu Visio albo język specyficzny dla domeny (DSL) lub model UML lub może to być zwykły tekst. Może być rozmieszczony w kilku plikach. Zwykle więcej niż jeden szablon odczytuje jeden model.

     Implikacje okresu "model" polega na tym, że reprezentuje jakiś aspekt firmy bezpośrednio niż wygenerowany kod programu lub inne pliki. Na przykład może przedstawiać plan sieci komunikacyjnej, która będzie nadzorować wygenerowanego oprogramowania.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Co to jest korzyść z używania szablonów tekstowych?
 Zazwyczaj generuje się wiele różnych kodów lub innych plików z jednego modelu. Model reprezentuje wymagania bezpośrednio od wygenerowanego kodu. Pomija szczegóły implementacji i jest zapisywana zgodnie z wymaganiami, a nie z kodem. Gdy wymagania zmieniają się — jak zwykle — można aktualizować model łatwiej i bardziej niezawodnie niż różne części kodu programu.

 W związku z tym generowanie kodu jest cennym narzędziem z perspektywy metod programowania Agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Co to są najlepsze rozwiązania dotyczące szablonów tekstowych?

- Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Co to jest "T4"?

- Inna nazwa dla funkcji szablonu tekstu programu Visual Studio opisana tutaj. Starsza wersja, która nie została opublikowana, była skrótem "transformacji szablonu tekstu".
