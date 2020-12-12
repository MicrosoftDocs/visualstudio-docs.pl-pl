---
title: Bloki formantów szablonów tekstowych
description: Dowiedz się więcej na temat bloków formantów szablonów tekstowych i sposobu, w jaki bloki sterujące umożliwiają pisanie kodu w szablonie tekstowym w celu zróżnicowania danych wyjściowych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11cc289f668a674707c584396998ea7abb9e7ea9
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363591"
---
# <a name="text-template-control-blocks"></a>Bloki formantów szablonów tekstowych
Bloki sterujące umożliwiają pisanie kodu w szablonie tekstowym w celu zróżnicowania danych wyjściowych. Istnieją trzy rodzaje bloków sterowania, które są rozróżniane przez ich nawiasy otwierające:

- `<# Standard control blocks #>` może zawierać instrukcje.

- `<#= Expression control blocks #>` może zawierać wyrażenia.

- `<#+ Class feature control blocks #>` może zawierać metody, pola i właściwości.

## <a name="standard-control-block"></a>Standardowy blok kontrolny
 Standardowe bloki sterujące zawierają instrukcje. Na przykład następujący blok standardowy pobiera nazwy wszystkich atrybutów w dokumencie XML:

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

 Możesz osadzić zwykły tekst wewnątrz instrukcji złożonej, takiej jak `if` lub `for` . Na przykład ten fragment generuje linię wyjściową w każdej iteracji pętli:

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
> Zawsze używaj {...} Aby rozdzielić zagnieżdżone instrukcje zawierające osadzony zwykły tekst. Następujący przykład może nie funkcjonować prawidłowo:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Zamiast tego należy uwzględnić {nawiasy klamrowe} w następujący sposób:

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

## <a name="expression-control-block"></a>Blok kontroli wyrażenia
 Bloki sterujące wyrażenia są używane w kodzie, który zawiera ciągi do zapisania w pliku wyjściowym. Na przykład, przy użyciu powyższego przykładu, można wydrukować nazwy atrybutów do pliku wyjściowego, modyfikując blok kodu w następujący sposób:

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

## <a name="class-feature-control-block"></a>Blok sterowania cechą klasy
 Można użyć bloków kontroli funkcji klasy, aby dodać metody, właściwości, pola, a nawet zagnieżdżone klasy do szablonu tekstu. Najbardziej typowym zastosowaniem bloków funkcji klasy jest dostarczanie funkcji pomocnika dla kodu w innych częściach szablonu tekstu. Na przykład następująca funkcja klasy blokuje pierwszą literę nazwy atrybutu (lub, jeśli nazwa zawiera odstępy, wielką literą każdego wyrazu):

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
> Po bloku sterowania funkcją klasy nie mogą następować standardowe bloki kontrolne w tym samym pliku szablonu. Jednak to ograniczenie nie dotyczy wyniku stosowania `<#@include#>` dyrektyw. Każdy dołączony plik może mieć bloki standardowe, a następnie bloki funkcji klasy.

 Można utworzyć funkcję, która generuje dane wyjściowe przez osadzenie bloków tekstowych i wyrażeń wewnątrz bloku sterowania funkcją klasy. Na przykład:

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

 Możesz wywołać tę funkcję z bloku standardowego lub z innego bloku funkcji klasy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Jak używać bloków sterowania
 Cały kod we wszystkich blokach standardowego i wyrażenia kontroli w pojedynczym szablonie (w tym cały kod w dołączonych szablonach) jest połączony z formularzem `TransformText()` metody wygenerowanego kodu. (Aby uzyskać więcej informacji na temat dołączania innych szablonów tekstowych do `include` dyrektywy, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md)).

 Podczas używania bloków sterowania należy pamiętać o następujących kwestiach:

- **Językowe.** W szablonie tekstowym można użyć kodu w języku C# lub Visual Basic. Językiem domyślnym jest C#, ale można określić Visual Basic przy użyciu `language` parametru `template` dyrektywy. (Aby uzyskać więcej informacji na temat `template` dyrektywy, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md)).

     Język używany w blokach kontroli nie ma nic robić z językiem lub formatem tekstu wygenerowanego w szablonie tekstowym. Można wygenerować C# przy użyciu kodu Visual Basic lub odwrotnie.

     W danym szablonie tekstowym można używać tylko jednego języka, w tym wszystkich szablonów tekstowych zawartych w `include` dyrektywie.

- **Zmienne lokalne.** Ponieważ cały kod w blokach Standard i Expression Control w szablonie tekstowym jest generowany jako pojedyncza Metoda, należy upewnić się, że nie występują żadne konflikty z nazwami zmiennych lokalnych. W przypadku dołączania innych szablonów tekstu należy się upewnić, że nazwy zmiennych są unikatowe we wszystkich dołączonych szablonach. Jednym ze sposobów upewnienia się, że jest dodanie ciągu do każdej nazwy zmiennej lokalnej identyfikującej szablon tekstu, w którym został zadeklarowany.

     Dobrym pomysłem jest również zainicjowanie zmiennych lokalnych w celu uzyskania rozsądnych wartości podczas ich deklarowania, szczególnie w przypadku dołączania wielu szablonów tekstowych.

- **Zagnieżdżanie bloków sterujących.** Bloki sterujące nie mogą być zagnieżdżone wewnątrz siebie. Należy zawsze przerwać dany blok kontroli przed otwarciem kolejnego. Na przykład, poniżej pokazano, jak wydrukować jakiś tekst w bloku wyrażenia jako część standardowego bloku sterowania.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refaktoryzacji.** Aby zachować czytelność szablonów tekstu i ułatwić ich zrozumienie, zdecydowanie zalecamy uniknięcie powtarzania kodu przez umieszczenie kodu wielokrotnego użytku w funkcjach pomocniczych w blokach funkcji klasy lub przez utworzenie własnej klasy szablonu tekstu, która dziedziczy z klasy Microsoft. VisualStudio. TextTemplating. TextTransformation.
