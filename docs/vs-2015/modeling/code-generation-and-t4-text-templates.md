---
title: Generowanie kodu i szablony tekstu T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667919"
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], *szablon tekstu T4* jest kombinacją bloków tekstowych i logiki formantów, które mogą generować plik tekstowy. Logika formantów jest zapisywana jako fragmenty kodu programu w [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. W programie Visual Studio 2015 Update 2 i nowszych można używać C# funkcji wersji 6,0 w dyrektywach szablonów T4. Wygenerowany plik może być tekstem dowolnego rodzaju, takim jak strona sieci Web lub plik zasobów lub kod źródłowy programu w dowolnym języku.

 Istnieją dwa rodzaje szablonów tekstu T4:

 **Szablony tekstu T4** ("wstępnie przetworzone") są wykonywane w aplikacji w celu utworzenia ciągów tekstowych, zazwyczaj jako części danych wyjściowych.
Na przykład można utworzyć szablon do definiowania strony HTML:

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

 Aplikacja może działać na komputerze, na którym nie zainstalowano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Aby utworzyć szablon czasu wykonywania, Dodaj **wstępnie przetworzony plik szablonu tekstu** do projektu. Alternatywnie możesz dodać zwykły plik tekstowy i ustawić jego właściwość **niestandardowego narzędzia** na **TextTemplatingFilePreprocessor**.

 Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

 **Szablony tekstu T4 w czasie projektowania** są wykonywane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby zdefiniować część kodu źródłowego i innych zasobów aplikacji.
Zazwyczaj można używać kilku szablonów, które odczytują dane w pojedynczym pliku wejściowym lub w bazie danych, i generują niektóre `.cs`, `.vb` lub inne pliki źródłowe. Każdy szablon generuje jeden plik. Są one wykonywane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].

 Na przykład dane wejściowe mogą być plikiem XML danych konfiguracyjnych. Za każdym razem, gdy edytujesz plik XML podczas opracowywania, szablony tekstowe spowodują ponowne wygenerowanie części kodu aplikacji. Jeden z szablonów może wyglądać podobnie do poniższego przykładu:

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 W zależności od wartości w pliku XML wygenerowany plik `.cs` będzie wyglądać następująco:

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

## <a name="in-this-section"></a>W tej sekcji
 [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md) W przypadku aplikacji generujących pliki tekstowe prekompilowane szablony tekstu są łatwą i niezawodną metodą definiowania tekstu. Nie można jednak użyć tej metody dla szablonów tekstowych, które zmieniają się w czasie wykonywania.

 [Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Generowanie kodu i innych zasobów z modelu umożliwia zaktualizowanie aplikacji przez zaktualizowanie modelu.

 [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md) Jeśli zainstalowano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Wizualizacja i Modeling SDK, możesz zapewnić aktualność wygenerowanego oprogramowania przy użyciu zmian w modelu.

 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md) Składnia pliku szablonu tekstu.

 [Przewodnik: generowanie kodu przy użyciu szablonów tekstowych](../modeling/walkthrough-generating-code-by-using-text-templates.md) Prezentacja jednego ze sposobów korzystania z generowania kodu.

 [Debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md) Debugowanie szablonów tekstowych i niektórych typowych błędów szablonów tekstowych.

 [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) Narzędzie wiersza polecenia, za pomocą którego można uruchamiać przekształcenia szablonu tekstu.

 [Dostosowywanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md) Pisanie procesorów dyrektywy i niestandardowych hostów tworzenia szablonów dla własnych źródeł danych.

## <a name="see-also"></a>Zobacz też
 [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md) [generujących kod z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
