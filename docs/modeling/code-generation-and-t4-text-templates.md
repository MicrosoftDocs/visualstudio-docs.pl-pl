---
title: Generowanie kodu i szablony tekstowe T4
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0eba8b4850ee845414084ef766fce30f9efd7e6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597207"
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4

W programie Visual Studio *szablon tekstu T4* jest kombinacją bloków tekstowych i logiki formantów, które mogą generować plik tekstowy. Logika formantów jest zapisywana jako fragmenty kodu programu w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. W programie Visual Studio 2015 Update 2 i nowszych można używać C# funkcji wersji 6,0 w dyrektywach szablonów T4. Wygenerowany plik może być tekstem dowolnego rodzaju, takim jak strona sieci Web lub plik zasobów lub kod źródłowy programu w dowolnym języku.

Istnieją dwa rodzaje szablonów tekstu T4: czas wykonywania i czas projektowania.

## <a name="run-time-t4-text-templates"></a>Szablony tekstu T4 w czasie wykonywania

Szablony czasu wykonywania są również nazywane szablonami "wstępnie przetworzony", ale są wykonywane w aplikacji w celu utworzenia ciągów tekstowych, zazwyczaj jako części danych wyjściowych. Na przykład można utworzyć szablon do definiowania strony HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Zauważ, że szablon przypomina wygenerowane dane wyjściowe. Podobieństwo szablonu do wynikowych danych wyjściowych pozwala uniknąć błędów, gdy użytkownik chce go zmienić.

Ponadto szablon zawiera fragmenty kodu programu. Za pomocą tych fragmentów można powtarzać sekcje tekstu, tworzyć sekcje warunkowe i wyświetlać dane z aplikacji.

Aby wygenerować dane wyjściowe, aplikacja wywołuje funkcję, która jest generowana przez szablon. Na przykład:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Aplikacja może działać na komputerze, na którym nie zainstalowano programu Visual Studio.

Aby utworzyć szablon czasu wykonywania, Dodaj **wstępnie przetworzony plik szablonu tekstu** do projektu. Alternatywnie możesz dodać zwykły plik tekstowy i ustawić jego właściwość **niestandardowego narzędzia** na **TextTemplatingFilePreprocessor**.

Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Szablony tekstu T4 w czasie projektowania

Szablony czasu projektowania definiują część kodu źródłowego i innych zasobów aplikacji. Zwykle używasz kilku szablonów, które odczytują dane w pojedynczym pliku wejściowym lub w bazie danych, i wygenerujesz niektóre z plików *. cs*, *. vb*lub inne pliki źródłowe. Każdy szablon generuje jeden plik. Są one wykonywane w programie Visual Studio lub MSBuild.

Na przykład dane wejściowe mogą być plikiem XML danych konfiguracyjnych. Za każdym razem, gdy edytujesz plik XML podczas opracowywania, szablony tekstowe ponownie generują część kodu aplikacji. Jeden z szablonów może wyglądać podobnie do poniższego przykładu:

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

W zależności od wartości w pliku XML wygenerowany plik *CS* będzie wyglądać następująco:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Innym przykładem jest to, że dane wejściowe mogą być diagramem przepływu pracy w działaniu biznesowym. Gdy użytkownicy zmieniają swój biznesowy przepływ pracy lub po rozpoczęciu pracy z nowymi użytkownikami, którzy mają inny przepływ pracy, można łatwo ponownie wygenerować kod w celu dopasowania go do nowego modelu.

Szablony czasu projektowania umożliwiają szybsze i bardziej niezawodne Zmienianie konfiguracji w przypadku zmiany wymagań. Zwykle dane wejściowe są zdefiniowane w wymaganiach firmy, jak w przykładowym przepływie pracy. Dzięki temu można łatwiej omówić zmiany z użytkownikami. Szablony czasu projektowania są dlatego przydatnym narzędziem w procesie programowania Agile.

Aby utworzyć szablon czasu projektowania, Dodaj plik **szablonu tekstu** do projektu. Alternatywnie możesz dodać zwykły plik tekstowy i ustawić jego właściwość **niestandardowego narzędzia** na **TextTemplatingFileGenerator**.

Aby uzyskać więcej informacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Termin *model* jest czasami używany do opisywania danych odczytywanych przez jeden lub więcej szablonów. Model może być w dowolnym formacie w dowolnym rodzaju pliku lub bazy danych. Nie musi być modelem UML ani modelem języka specyficznym dla domeny. "Model" oznacza, że dane mogą być zdefiniowane w warunkach koncepcji biznesowej, a nie podobne do kodu.

Funkcja transformacji szablonu tekstu jest nazywana *T4*.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
