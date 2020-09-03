---
title: Dyrektywa importu T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4a931ca05f8b12175deded8b316d0177d8f8c74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661817"
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W blokach kodu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstu T4 `import` dyrektywa pozwala odwoływać się do elementów w innej przestrzeni nazw bez podawania w pełni kwalifikowanej nazwy. Jest odpowiednikiem `using` w języku C# lub `imports` w [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] .

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
 [Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)
