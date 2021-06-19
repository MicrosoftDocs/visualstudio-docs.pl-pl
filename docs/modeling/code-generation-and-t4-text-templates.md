---
title: Generowanie kodu i szablony tekstowe T4
description: Dowiedz się, jak szablon tekstowy T4 to połączenie bloków tekstowych i logiki sterującej, która może generować plik tekstowy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76714be09c38f6426626e94ee7734873c823f704
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389777"
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4

W Visual Studio szablon *tekstowy T4* to połączenie bloków tekstowych i logiki sterującej, która może wygenerować plik tekstowy. Logika sterowania jest zapisywana jako fragmenty kodu programu w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] programie lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . W Visual Studio 2015 Update 2 i nowszych można używać funkcji języka C# w wersji 6.0 w dyrektywach szablonów T4. Wygenerowany plik może być tekstem dowolnego rodzaju, takim jak strona internetowa, plik zasobów lub kod źródłowy programu w dowolnym języku.

Istnieją dwa rodzaje szablonów tekstowych T4: czas uruchamiania i czas projektowania.

## <a name="run-time-t4-text-templates"></a>Szablony tekstowe T4 czasu uruchamiania

Szablony czasu wykonywania, nazywane również "wstępnie przetworzonymi" szablonami, są wykonywane w aplikacji w celu tworzenia ciągów tekstowych, zwykle jako część danych wyjściowych. Można na przykład utworzyć szablon w celu zdefiniowania strony HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Zwróć uwagę, że szablon przypomina wygenerowane dane wyjściowe. Podobieństwo szablonu do wynikowych danych wyjściowych pomaga uniknąć błędów, gdy chcesz go zmienić.

Ponadto szablon zawiera fragmenty kodu programu. Możesz użyć tych fragmentów, aby powtórzyć sekcje tekstu, utworzyć sekcje warunkowe i wyświetlić dane z aplikacji.

Aby wygenerować dane wyjściowe, aplikacja wywołuje funkcję wygenerowaną przez szablon. Na przykład:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Aplikację można uruchomić na komputerze, na Visual Studio zainstalowana.

Aby utworzyć szablon czasu uruchomienia, dodaj **do** projektu wstępnie przetworzony plik szablonu tekstowego. Alternatywnie można dodać plik w postaci zwykłego tekstu i ustawić jego właściwość **Custom Tool** na **wartość TextTemplatingFilePreprocessor.**

Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md) Aby uzyskać więcej informacji na temat składni szablonów, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

## <a name="design-time-t4-text-templates"></a>Szablony tekstowe T4 czasu projektowania

Szablony czasu projektowania definiują część kodu źródłowego i innych zasobów aplikacji. Zazwyczaj używasz kilku szablonów, które odczytuje dane w jednym pliku wejściowym lub bazie danych i generuje niektóre pliki *.cs,* *vb* lub inne pliki źródłowe. Każdy szablon generuje jeden plik. Są one wykonywane w Visual Studio lub MSBuild.

Na przykład dane wejściowe mogą być plikiem XML danych konfiguracji. Każdorazowo podczas edytowania pliku XML szablony tekstowe ponownie generują część kodu aplikacji. Jeden z szablonów może wyglądać następująco:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

W zależności od wartości w pliku XML wygenerowany plik *cs* będzie wyglądać następująco:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Innym przykładem może być diagram przepływu pracy w działaniu biznesowym. Gdy użytkownicy zmieniają swój biznesowy przepływ pracy lub gdy rozpoczynasz pracę z nowymi użytkownikami, którzy mają inny przepływ pracy, można łatwo ponownie wygenerować kod, aby dopasować go do nowego modelu.

Szablony czasu projektowania sprawiają, że zmiana konfiguracji w przypadku zmiany wymagań jest szybsza i bardziej niezawodna. Zazwyczaj dane wejściowe są definiowane w kategoriach wymagań biznesowych, jak w przykładzie przepływu pracy. Ułatwia to omawianie zmian z użytkownikami. Szablony czasu projektowania są więc przydatnym narzędziem w procesie projektowania zwinnego.

Aby utworzyć szablon czasu projektowania, dodaj plik **szablonu tekstowego** do projektu. Alternatywnie można dodać plik w postaci zwykłego tekstu i ustawić jego właściwość **Custom Tool** na **wartość TextTemplatingFileGenerator.**

Aby uzyskać więcej informacji, zobacz Design-Time Code Generation by using T4 Text Templates (Generowanie kodu [w czasie projektowania przy użyciu szablonów tekstowych T4).](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Aby uzyskać więcej informacji na temat składni szablonów, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Termin *model jest* czasami używany do opisywania danych odczytywanych przez co najmniej jeden szablon. Model może być w dowolnym formacie, w dowolnym rodzaju pliku lub bazy danych. Nie musi to być model UML ani Domain-Specific Language. "Model" oznacza po prostu, że dane można zdefiniować w kategoriach pojęć biznesowych, zamiast przypominać kod.

Funkcja przekształcania szablonu tekstu nosi nazwę *T4*.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
