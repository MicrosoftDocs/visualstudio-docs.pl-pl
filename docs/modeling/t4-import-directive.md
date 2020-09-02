---
title: Dyrektywa T4 dotycząca importowania
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a28bedd01e3a4f6a7a87b025ac9a9a6184da9b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591869"
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
