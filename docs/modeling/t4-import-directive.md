---
title: Dyrektywa T4 dotycząca importowania
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1165a966a532dcb9f07bbc1e46f08a1cb26de161
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748202"
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania

W blokach kodu szablonu tekstu T4 programu Visual Studio dyrektywa `import` umożliwia odwoływanie się do elementów w innej przestrzeni nazw bez podawania w pełni kwalifikowanej nazwy. Jest to odpowiednik `using` w C# lub `imports` w [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

## <a name="see-also"></a>Zobacz także

- [Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)