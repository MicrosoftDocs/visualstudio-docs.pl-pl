---
title: Generowanie szablonu tekstu na podstawie szablonu tekstowego
description: Zawiera informacje o sposobach generowania szablonu tekstu z innego szablonu tekstu przy użyciu sekwencji unikowych.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d7ef983525842023247433e7a3c2b51e206a1cee
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100764"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Porady: generowanie szablonów z szablonów przy użyciu sekwencji unikowych
Można utworzyć szablon tekstu, który tworzy inny szablon tekstowy jako wygenerowany tekst wyjściowy. W tym celu należy użyć sekwencji unikowych, aby odróżnić Tagi szablonu tekstu. Jeśli nie używasz sekwencji unikowych, wygenerowany szablon tekstu będzie miał wstępnie zdefiniowane znaczenie. Aby uzyskać więcej informacji o używaniu sekwencji ucieczki w szablonach tekstowych, zobacz [Używanie sekwencji unikowych w szablonach tekstowych](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Aby wygenerować szablon tekstowy z poziomu szablonu tekstowego

- Użyj ukośnika odwrotnego ( \\ ) jako znaku ucieczki, aby utworzyć niezbędne znaczniki znaczników w szablonie tekstowym dla dyrektyw, instrukcji, wyrażeń i funkcji klasy w osobnym pliku szablonu tekstowego.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Przykład
 Poniższy przykład używa znaków ucieczki, aby utworzyć szablon tekstowy z szablonu tekstu. `output`Dyrektywa ustawia typ pliku docelowego na typ pliku szablonu tekstu (. tt).

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

 Wygenerowany tekst wyjściowy jest szablonem tekstowym.

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
