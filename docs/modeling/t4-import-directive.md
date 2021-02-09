---
title: Dyrektywa T4 dotycząca importowania
description: Dowiedz się, że w szablonie tekstowym programu Visual Studio T4 dyrektywa import umożliwia odwoływanie się do elementów w innej przestrzeni nazw bez podawania w pełni kwalifikowanej nazwy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9eb50261b346d8751a76817d97d59a798d17236
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899667"
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania

W blokach kodu szablonu tekstu T4 programu Visual Studio `import` dyrektywa pozwala odwoływać się do elementów w innej przestrzeni nazw bez podawania w pełni kwalifikowanej nazwy. Jest odpowiednikiem `using` w języku C# lub `imports` w [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] .

Aby uzyskać ogólne omówienie pisania szablonów tekstowych T4, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

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
