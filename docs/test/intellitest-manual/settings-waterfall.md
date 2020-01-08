---
title: Ustawienia kaskadowe | Narzędzie testowe dla deweloperów Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 95a2029cee1fd13241aba727f671a164d7272543
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591583"
---
# <a name="settings-waterfall"></a>Kaskadowy model ustawień

Koncepcja ustawień kaskadowych oznacza, że użytkownik może określić ustawienia na poziomie **zestawu**, **osprzętu**i **eksploracji** :

* Zestaw — [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Armatura — [PexClass](attribute-glossary.md#pexclass)
* Eksploracja — [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone na poziomie **zestawu** mają wpływ na wszystkie armaturę i eksplorację w tym zestawie. Ustawienia określone na poziomie **armatury** mają wpływ na wszystkie eksploracje w ramach tej armatury. Ustawienia podrzędne win&mdash;, jeśli ustawienie jest zdefiniowane na poziomie **zestawu** i poziomów **armatury** , są używane ustawienia **osprzętu** .

Należy zauważyć, że niektóre ustawienia są specyficzne dla poziomu **zestawu** lub poziomu **osprzętu** .

**Przykład**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Chcesz przekazać opinię?

Publikuj swoje pomysły i żądania funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
