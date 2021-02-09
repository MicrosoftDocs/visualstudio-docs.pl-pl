---
title: Generowanie szablonu tekstu na podstawie szablonu tekstowego
description: Zawiera informacje o sposobach generowania szablonu tekstu z innego szablonu tekstu przy użyciu sekwencji unikowych.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: e3debeeafa55e483e9625c67534694debff6acfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922791"
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
