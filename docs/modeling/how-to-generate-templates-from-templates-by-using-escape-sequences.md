---
title: 'Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35047c6c0887d02f3adcba763de05b8d4a1cd00b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993197"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki
Można utworzyć szablon tekstowy, który tworzy inny szablon tekstowy jako dane wyjściowe wygenerowanego tekstu. Aby to zrobić, należy użyć sekwencje ucieczki aby odróżnić tagi szablonu tekstu. Jeśli nie korzystanie z sekwencji ucieczki, szablon wygenerowany tekst będzie mieć znaczenie wstępnie zdefiniowane. Aby uzyskać więcej informacji na temat przy użyciu sekwencji unikowych w szablonach tekstowych, zobacz [przy użyciu sekwencji unikowych w szablonach tekstowych](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Aby wygenerować z szablonu tekstu w szablonie tekstu

- Użyj ukośnik odwrotny (\\) jako znak ucieczki do produkcji niezbędne znaczniki w szablonie tekstu dla dyrektywy, instrukcje, wyrażenia i funkcji w pliku szablonu tekstu oddzielne klasy.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto znaki ucieczki, aby utworzyć szablon tekstowy z szablonu tekstu. `output` Dyrektywa określa docelowy typ pliku z typem pliku szablonu tekstu (.tt).

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

 Wygenerowany tekst wyjściowy jest szablonu tekstu.

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