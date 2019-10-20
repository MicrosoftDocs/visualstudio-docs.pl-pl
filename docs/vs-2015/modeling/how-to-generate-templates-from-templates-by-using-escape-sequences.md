---
title: 'Instrukcje: generowanie szablonów z szablonów przy użyciu sekwencji unikowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 501b7f040cb841d19c06ccc8fe7615a5b4a5e70d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657343"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Porady: generowanie szablonów z szablonów przy użyciu sekwencji unikowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć szablon tekstu, który tworzy inny szablon tekstowy jako wygenerowany tekst wyjściowy. W tym celu należy użyć sekwencji unikowych, aby odróżnić Tagi szablonu tekstu. Jeśli nie używasz sekwencji unikowych, wygenerowany szablon tekstu będzie miał wstępnie zdefiniowane znaczenie. Aby uzyskać więcej informacji o używaniu sekwencji ucieczki w szablonach tekstowych, zobacz [Używanie sekwencji unikowych w szablonach tekstowych](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Aby wygenerować szablon tekstowy z poziomu szablonu tekstowego

- Użyj ukośnika odwrotnego (\\) jako znaku ucieczki, aby utworzyć niezbędne znaczniki znaczników w szablonie tekstowym dla dyrektyw, instrukcji, wyrażeń i funkcji klasy w osobnym pliku szablonu tekstowego.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Przykład
 Poniższy przykład używa znaków ucieczki, aby utworzyć szablon tekstowy z szablonu tekstu. Dyrektywa `output` ustawia typ pliku docelowego na typ pliku szablonu tekstu (. tt).

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
