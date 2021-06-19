---
title: Generowanie szablonu tekstowego na podstawie szablonu tekstowego
description: Zawiera informacje na temat sposobu generowania szablonu tekstu na podstawie innego szablonu tekstowego przy użyciu sekwencji ucieczki.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9347e32a72e7f590f8f513c4b47a4b7aae699f27
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387180"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Porady: generowanie szablonów z szablonów przy użyciu sekwencji unikowych
Możesz utworzyć szablon tekstowy, który tworzy inny szablon tekstowy jako wygenerowane dane wyjściowe tekstu. Aby to zrobić, należy użyć sekwencji ucieczki do oznaczenia tagów szablonu tekstu. Jeśli nie używasz sekwencji ucieczki, wygenerowany szablon tekstu będzie miał wstępnie zdefiniowane znaczenie. Aby uzyskać więcej informacji na temat używania sekwencji ucieczki w szablonach tekstowych, zobacz Using Escape Sequences in Text Templates (Używanie [sekwencji ucieczki w szablonach tekstowych).](../modeling/using-escape-sequences-in-text-templates.md)

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Aby wygenerować szablon tekstowy z poziomu szablonu tekstowego

- Użyj ukośnika odwrotnego ( ) jako znaku ucieczki, aby utworzyć niezbędne tagi znaczników w szablonie tekstowym dla dyrektyw, instrukcji, wyrażeń i cech klasy w oddzielnym pliku \\ szablonu tekstowego.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto znaków ucieczki, aby utworzyć szablon tekstowy na podstawie szablonu tekstowego. Dyrektywa `output` ustawia typ pliku docelowego na typ pliku szablonu tekstowego (.tt).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 Wygenerowane dane wyjściowe tekstu są szablonem tekstowym.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
