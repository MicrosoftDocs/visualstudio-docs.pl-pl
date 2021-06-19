---
title: Bloki formantów szablonów tekstowych
description: Dowiedz się więcej o blokach sterujących szablonu tekstu i o tym, jak bloki sterujące umożliwiają pisanie kodu w szablonie tekstowym w celu zmiany danych wyjściowych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90a4efea7d37b83d3d5ff7a085abcf3439d99263
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388727"
---
# <a name="text-template-control-blocks"></a>Bloki formantów szablonów tekstowych
Bloki sterujące umożliwiają pisanie kodu w szablonie tekstowym w celu zmiany danych wyjściowych. Istnieją trzy rodzaje bloków sterujących, które odróżniają nawiasy otwierające:

- `<# Standard control blocks #>` może zawierać instrukcje .

- `<#= Expression control blocks #>` może zawierać wyrażenia.

- `<#+ Class feature control blocks #>` Może zawierać metody, pola i właściwości.

## <a name="standard-control-block"></a>Blok kontrolki standardowej
 Standardowe bloki sterujące zawierają instrukcje . Na przykład następujący blok standardowy pobiera nazwy wszystkich atrybutów w dokumencie XML:

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

 Zwykły tekst można osadzić wewnątrz instrukcji złożonej, takiej jak `if` lub `for` . Na przykład ten fragment generuje wiersz wyjściowy w każdej iteracji pętli:

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
> Zawsze używaj {...} do rozdzielania zagnieżdżonych instrukcji zawierających osadzony zwykły tekst. Poniższy przykład może nie działać prawidłowo:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Zamiast tego należy dołączyć nawiasy klamrowe {braces}, w następujący sposób:

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

## <a name="expression-control-block"></a>Blok sterowania wyrażeniami
 Bloki sterowania wyrażeniami są używane dla kodu, który udostępnia ciągi, które mają być zapisywane w pliku wyjściowym. Na przykład w powyższym przykładzie można wydrukować nazwy atrybutów w pliku wyjściowym, modyfikując blok kodu w następujący sposób:

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

## <a name="class-feature-control-block"></a>Blok sterowania cechami klas
 Bloków sterowania cechami klas można używać do dodawania metod, właściwości, pól, a nawet klas zagnieżdżonych do szablonu tekstu. Najpowszechniejszym zastosowaniem bloków cech klasy jest zapewnienie funkcji pomocnika dla kodu w innych częściach szablonu tekstu. Na przykład poniższy blok funkcji klasy zawiera pierwszą literę nazwy atrybutu (lub, jeśli nazwa zawiera odstęp, pierwsza litera każdego wyrazu jest oznaczana literą pierwszą):

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
> Po bloku sterowania cechami klas nie mogą znajdować się standardowe bloki sterujące w tym samym pliku szablonu. Jednak to ograniczenie nie ma zastosowania do wyniku dyrektyw `<#@include#>` using. Każdy dołączony plik może mieć standardowe bloki, po których następuje blok funkcji klasy.

 Możesz utworzyć funkcję, która generuje dane wyjściowe, osadzając bloki tekstu i wyrażeń wewnątrz bloku sterowania cechami klasy. Na przykład:

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

 Tę funkcję można wywołać z bloku standardowego lub z innego bloku funkcji klasy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Jak używać bloków sterowania
 Cały kod we wszystkich standardowych blokach sterujących wyrażeniami i wyrażeniach w jednym szablonie (w tym cały kod w uwzględnionych szablonach) jest połączony w celu tworzenia `TransformText()` metody wygenerowanego kodu. (Aby uzyskać więcej informacji na temat do uwzględnienia innych szablonów tekstowych z `include` dyrektywą , zobacz [dyrektywy T4 dotyczące szablonów tekstowych).](../modeling/t4-text-template-directives.md)

 W przypadku używania bloków sterujących należy pamiętać o następujących kwestiach:

- **Język.** W szablonie tekstowym można użyć Visual Basic c# lub kodu. Język domyślny to C#, ale można Visual Basic za pomocą `language` parametru `template` dyrektywy . (Aby uzyskać więcej informacji na temat `template` dyrektywy , zobacz dyrektywy [T4 dotyczące szablonów tekstowych).](../modeling/t4-text-template-directives.md)

     Język używany w blokach sterujących nie ma nic wspólnego z językiem ani formatem tekstu wygenerowanego w szablonie tekstu. Język C# można wygenerować przy użyciu Visual Basic lub odwrotnie.

     W danym szablonie tekstowym można używać tylko jednego języka, w tym wszystkich szablonów tekstowych dołączanych do `include` dyrektywy .

- **Zmienne lokalne.** Ponieważ cały kod w standardowych blokach sterujących wyrażeniami i w szablonie tekstowym jest generowany jako pojedyncza metoda, należy upewnić się, że nie ma żadnych konfliktów z nazwami zmiennych lokalnych. Jeśli uwzględniasz inne szablony tekstowe, upewnij się, że nazwy zmiennych są unikatowe dla wszystkich dołączonych szablonów. Jednym ze sposobów zapewnienia tego jest dodanie ciągu do każdej nazwy zmiennej lokalnej identyfikującej szablon tekstowy, w którym został zadeklarowany.

     Dobrym pomysłem jest również zainicjowanie zmiennych lokalnych w celu uwzględnienia sensownych wartości podczas ich deklarowania, szczególnie w przypadku uwzględnienia wielu szablonów tekstowych.

- **Zagnieżdżanie bloków sterujących.** Bloki sterujące mogą nie być zagnieżdżone wewnątrz siebie. Należy zawsze zakończyć dany blok sterujący przed otwarciem kolejnego. Na przykład poniżej przedstawiono sposób drukowania tekstu w bloku wyrażeń jako części standardowego bloku sterującego.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refaktoryzacji.** Aby szablony tekstowe były krótkie i łatwe do zrozumienia, zdecydowanie zaleca się unikanie powtarzalnego kodu przez faktorowanie kodu wielokrotnego użytku w funkcjach pomocnika w blokach cech klasy lub przez utworzenie własnej klasy szablonu tekstu dziedziczonej z klasy Microsoft.VisualStudio.TextTemplating.TextTransformation.
