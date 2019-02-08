---
title: Bloki formantów szablonów tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 939198eb18dd8fd572f1bd5bf3f4a21b44a5cf2d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936970"
---
# <a name="text-template-control-blocks"></a>Bloki formantów szablonów tekstowych
Bloki sterujące umożliwiają pisanie kodu w szablonie tekstowym w celu różnią się w danych wyjściowych. Istnieją trzy rodzaje bloki sterujące, które są rozróżniane na podstawie ich otwierające nawiasy:

-   `<# Standard control blocks #>` może zawierać instrukcji.

-   `<#= Expression control blocks #>` może zawierać wyrażeń.

-   `<#+ Class feature control blocks #>` może zawierać metody, pola i właściwości.

## <a name="standard-control-block"></a>Standardowy blok sterujący
 Standardowe bloki sterujące zawierają instrukcje. Na przykład poniższy blok standardowa pobiera nazwy wszystkich atrybutów w dokumencie XML:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Można osadzić jako zwykły tekst wewnątrz instrukcji złożonej, takich jak `if` lub `for`. Na przykład ten fragment generuje wiersza danych wyjściowych w każdej iteracji pętli:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
>  Zawsze używaj {...} Aby ograniczyć zagnieżdżonych instrukcji, które zawierają osadzony zwykły tekst. Poniższy przykład może nie działać prawidłowo:
>
>  `<# if (ShouldPrint) #> Some text. -- WRONG`
>
>  Zamiast tego powinien zawierać {nawiasów klamrowych}, w następujący sposób:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>Blok sterowania wyrażeniem
 Bloki sterowania wyrażeniami są używane dla kodu, który zawiera ciągi są zapisywane w pliku wyjściowego. Na przykład w powyższym przykładzie można wydrukować nazwy atrybutów do pliku wyjściowego, zmieniając następujący blok kodu:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Blok sterowania cechami klasy
 Bloki sterowania cechami klas umożliwia dodawanie metod, właściwości, pola lub klasy zagnieżdżone nawet do szablonu tekstu. Najczęściej używane bloki cech klas jest zapewnienie funkcji pomocnika dla kodu w innych częściach szablonu tekstu. Na przykład poniższy blok funkcji klasy zamienia pierwszą literę nazwy atrybutu na wielkie (lub, jeśli nazwa zawiera białe znaki, powoduje rozpoczynanie pierwszą literę każdego wyrazu):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
>  Blok sterowania cechami klasy nie musi następować standardowe bloki sterujące w tym samym pliku szablonu. Jednak to ograniczenie nie ma zastosowania do wyniku za pomocą `<#@include#>` dyrektywy. Każdy dołączony plik może mieć standardowe bloki, a następnie przez bloki cech klas.

 Można utworzyć funkcję, która generuje dane wyjściowe, osadzając blokami tekstu i wyrażenia wewnątrz blok sterowania cechami klasy. Na przykład:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Można wywołać tę funkcję, od standardowego bloku lub z innego bloku funkcji klasy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Jak używać bloki sterujące
 Cały kod w wszystkie bloki kontrolne standard i wyrażenia w pojedynczym szablonie (w tym cały kod w szablonach uwzględnione) jest połączony w celu utworzenia `TransformText()` metoda wygenerowanego kodu. (Aby uzyskać więcej informacji o tym innych szablonów tekstowych przy użyciu `include` dyrektywy, zobacz [dyrektywy T4 dotyczące szablonu tekstowego](../modeling/t4-text-template-directives.md).)

 Możesz należy mieć na uwadze następujące kwestie korzystając z bloków sterowania:

-   **Język.** C# lub kod języka Visual Basic można użyć w szablonie tekstu. Jest to domyślny język C#, ale można określić Visual Basic z `language` parametru `template` dyrektywy. (Aby uzyskać więcej informacji na temat `template` dyrektywy, zobacz [dyrektywy T4 dotyczące szablonu tekstowego](../modeling/t4-text-template-directives.md).)

     Język, którego używasz w bloki sterujące ma nic wspólnego z języka lub format tekstu, które można wygenerować w szablonie tekstu. Możesz wygenerować C# za pomocą języka Visual Basic kodu lub odwrotnie.

     Można użyć tylko jednego języka w szablonie danego tekstu, w tym szablony tekstowe zawierają dzięki `include` dyrektywy.

-   **Zmienne lokalne.** Ponieważ cały kod w formancie standard i wyrażeń, bloków w szablonie tekstowym zostanie wygenerowany jako pojedynczej metody, powinien należy upewnić się, że nie istnieją żadne konflikty z nazwami zmiennych lokalnych. W przypadku dołączania innych szablonów tekstowych upewnij się, że nazwy zmiennych są unikatowe w dołączane szablony. Jest jednym ze sposobów, aby upewnić się, to aby dodać parametry do każdego lokalna nazwa zmiennej, identyfikowanie szablonu tekstu, w którym został zadeklarowany.

     Jest również dobry pomysł, aby zainicjować rozsądne wartości zmiennych lokalnych, w przypadku deklarowania, szczególnie w przypadku, gdy w przypadku dołączania wielu szablonów tekstowych.

-   **Zagnieżdżanie bloków sterujących.** Bloki sterujące nie mogą być zagnieżdżone wewnątrz siebie nawzajem. Zawsze należy zakończyć bloku danej kontrolki, zanim otworzysz inny. Na przykład poniżej przedstawiono sposób drukowania tekst w bloku wyrażenia jako część standardowy blok sterujący.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

-   **Refaktoryzacji.** Aby zachować szablony tekstowe krótko- i łatwa do zrozumienia, zdecydowanie zaleca wyprowadzenie kodu wielokrotnego użytku do funkcji pomocnika w bloki cech klas lub tworząc własne klasy szablonu tekstu, która dziedziczy można uniknąć powtarzania kodu z klasy element Microsoft.VisualStudio.TextTemplating.TextTransformation.