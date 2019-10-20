---
title: Jak... z szablonami tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671617"
---
# <a name="how-to--with-text-templates"></a>How to ... with — Szablony tekstowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony tekstowe w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewniają przydatny sposób generowania tekstu dowolnego rodzaju. Za pomocą szablonów tekstowych można generować tekst w czasie wykonywania jako część aplikacji i w czasie projektowania, aby wygenerować część kodu projektu. W tym temacie przedstawiono podsumowanie najczęściej zaproszonych "Jak mogę...?" masz.

 W tym temacie wiele odpowiedzi, które są poprzedzone punktorami, są sugestiami alternatywnymi.

 Aby zapoznać się z ogólnym wprowadzeniem do szablonów tekstowych, przeczytaj temat [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Jak...

### <a name="generate-part-of-my-application-code"></a>Generuj część mojego kodu aplikacji
 Mam konfigurację lub *model* w pliku lub bazie danych. Co najmniej jedna część mojego kodu jest zależna od tego modelu.

- Generuj niektóre pliki kodu z szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) i [jaki jest najlepszy sposób rozpoczęcia pisania szablonu?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generowanie plików w czasie wykonywania, przekazywanie danych do szablonu
 W czasie wykonywania moja aplikacja generuje pliki tekstowe, takie jak raporty, które zawierają kombinację standardowego tekstu i danych. Chcę uniknąć pisania setek instrukcji `write`.

- Dodaj szablon tekstu środowiska uruchomieniowego do projektu. Ten szablon służy do tworzenia klasy w kodzie, którą można utworzyć i użyć do generowania tekstu. W parametrach konstruktora można przekazać do niego dane. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Jeśli chcesz generować z szablonów, które są dostępne tylko w czasie wykonywania, możesz użyć standardowych szablonów tekstowych. Jeśli piszesz rozszerzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz wywołać usługę Text tworzenia szablonów. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). W innych kontekstach można użyć aparatu tekstu tworzenia szablonów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Użyj dyrektywy \< # @parameter # > do przekazywania parametrów do tych szablonów. Aby uzyskać więcej informacji, zobacz [dyrektywa parametrów T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Odczytaj inny plik projektu z szablonu
 Aby odczytać plik z tego samego projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] co szablon:

- Wstaw `hostSpecific="true"` do dyrektywy `<#@template#>`.

     W kodzie Użyj `this.Host.ResolvePath(filename)`, aby uzyskać pełną ścieżkę pliku.

### <a name="invoke-methods-from-a-template"></a>Wywoływanie metod z szablonu
 Jeśli istnieją już metody, na przykład w standardowych klasach [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]:

- Użyj dyrektywy \< # @assembly # > do załadowania zestawu, a następnie użyj \< # @import # >, aby ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dyrektywa importowania T4](../modeling/t4-import-directive.md).

   Jeśli często używasz tego samego zestawu dyrektyw Assembly i import, rozważ zapisanie procesora dyrektywy. W każdym szablonie można wywołać procesor dyrektywy, który może ładować zestawy i pliki modelu i ustawić kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Jeśli piszesz metody samodzielnie:

- W przypadku pisania szablonu tekstu środowiska uruchomieniowego należy napisać częściową definicję klasy, która ma taką samą nazwę jak szablon tekstu środowiska uruchomieniowego. Dodaj dodatkowe metody do tej klasy.

- Napisz blok sterowania funkcją klasy `<#+ ... #>`, w którym można zadeklarować metody, właściwości i klasy prywatne. Po skompilowaniu szablonu tekstu jest on przekształcany w klasę. Bloki formantów standardowych `<#...#>` i Text są przekształcane na pojedynczą metodę, a bloki funkcji klasy są wstawiane jako osobne elementy członkowskie. Aby uzyskać więcej informacji, zobacz [bloki kontrolne szablonu tekstu](../modeling/text-template-control-blocks.md).

   Metody zdefiniowane jako funkcje klasy mogą również zawierać osadzone bloki tekstu.

   Rozważ umieszczenie funkcji klasy w osobnym pliku, który można `<#@include#>` do jednego lub kilku plików szablonów.

- Napisz metody w osobnym zestawie (bibliotece klas) i Wywołaj je z szablonu. Użyj dyrektywy `<#@assembly#>` do załadowania zestawu i `<#@import#>`, aby ustawić kontekst przestrzeni nazw. Należy pamiętać, że w celu odbudowania zestawu podczas jego debugowania może być konieczne zatrzymanie i ponowne uruchomienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generowanie wielu plików z jednego schematu modelu
 Jeśli często generowane są pliki z modeli, które mają ten sam schemat XML lub bazy danych:

- Rozważ zapisanie procesora dyrektywy. Pozwala to na zamianę wielu instrukcji zestawu i instrukcji importu w każdym szablonie z pojedynczą dyrektywą niestandardową. Procesor dyrektywy może również ładować i analizować plik modelu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generowanie plików z modelu złożonego

- Rozważ utworzenie języka specyficznego dla domeny (DSL) do reprezentowania modelu. Dzięki temu można znacznie łatwiej pisać szablony, ponieważ używasz typów i właściwości, które odzwierciedlają nazwy elementów w modelu. Nie jest konieczne analizowanie pliku ani nawigowanie po węzłach XML. Na przykład:

     `foreach (Book book in this.Library) { ... }`

     Aby uzyskać więcej informacji, zobacz [wprowadzenie z językami specyficznymi dla domeny](../modeling/getting-started-with-domain-specific-languages.md) i [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

- Rozważ wygenerowanie kodu z modelu UML. Kod nie musi bezpośrednio odzwierciedlać UML. Na przykład nie trzeba generować klasy dla każdej klasy w modelu UML. Zamiast tego można użyć diagramu klas UML do reprezentowania witryny sieci Web i wygenerować strony sieci Web na podstawie każdej klasy UML. Wybierz typ diagramu najbardziej zbliżony do Twoich potrzeb. Na przykład wybierz diagramy aktywności do reprezentowania dowolnego typu przepływu pracy. Można zdefiniować stereotypy, aby dodać informacje odpowiednie dla aplikacji do każdego typu elementu.

     Generowanie na podstawie modelu UML umożliwia narysowanie i edytowanie modelu w formularzu diagramowy, ale bez konieczności projektowania własnego typu diagramu, tak jak w przypadku DSL.

     Aby uzyskać więcej informacji, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md) i [generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).

### <a name="get-data-from-includevsprvsincludesvsprvs-mdmd"></a>Pobierz dane z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 Aby korzystać z usług oferowanych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ustaw atrybut `hostSpecific` i Załaduj zestaw `EnvDTE`. Na przykład:

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

### <a name="starting"></a>Co to jest najlepszy sposób na rozpoczęcie pisania szablonu tekstu?

1. Napisz konkretny przykład wygenerowanego pliku.

2. Przekształcenie go w szablon tekstowy przez wstawienie dyrektywy `<#@template #>` i dyrektyw i kodu, które są wymagane do załadowania pliku wejściowego lub modelu.

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

- Inna nazwa dla funkcji szablonu tekstu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] opisana tutaj. Starsza wersja, która nie została opublikowana, była skrótem "transformacji szablonu tekstu".
