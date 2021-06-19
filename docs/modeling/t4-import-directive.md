---
title: Dyrektywa T4 dotycząca importowania
description: Dowiedz się, że w Visual Studio tekstowym T4 dyrektywa import pozwala odwoływać się do elementów w innej przestrzeni nazw bez podaniem w pełni kwalifikowanej nazwy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0d441ec5a62dfa5266a17a06ac8fe33941136c6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386322"
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania

W blokach kodu szablonu Visual Studio T4 dyrektywa pozwala odwoływać się do elementów w innej przestrzeni nazw bez podaniem w `import` pełni kwalifikowanej nazwy. Jest to odpowiednik w `using` języku C# lub `imports` [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] w .

Aby uzyskać ogólne omówienie pisania szablonów tekstowych T4, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-import-directive"></a>Używanie dyrektywy Import

```
<#@ import namespace="namespace" #>
```

 W tym przykładzie kod szablonu może pominąć jawną przestrzeń nazw dla członków System.IO:

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Standardowe importowanie
 Następująca przestrzeń nazw jest importowana automatycznie, aby nie trzeba było pisać dla niej dyrektywy importu:

- `System`

  Ponadto, jeśli używasz niestandardowej dyrektywy, procesor dyrektywy mógłby automatycznie zaimportować niektóre przestrzenie nazw.

  Na przykład, jeśli piszesz szablony dla języka specyficznego dla domeny (domain-specific language — DSL), nie musisz pisać dyrektyw importu dla następujących przestrzeni nazw:

- `Microsoft.VisualStudio.Modeling`

- Przestrzeń nazw DSL

## <a name="see-also"></a>Zobacz też

- [Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)
