---
title: 'Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji unikowych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a3ddd7896732c5b87c5b6bd2032c27fffd96a41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109741"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
