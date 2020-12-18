---
title: Ustawienia kaskadowe | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: Dowiedz się więcej o ustawieniach kaskadowych, które organizują ustawienia na poziomie zestawu, osprzętu i eksploracji.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2ca1cdcc1da97f8fa0d5def89e4f437607b36dd9
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668758"
---
# <a name="settings-waterfall"></a>Kaskadowy model ustawień

Koncepcja ustawień kaskadowych oznacza, że użytkownik może określić ustawienia na poziomie **zestawu**, **osprzętu** i **eksploracji** :

* Zestaw — [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Armatura — [PexClass](attribute-glossary.md#pexclass)
* Eksploracja — [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone na poziomie **zestawu** mają wpływ na wszystkie armaturę i eksplorację w tym zestawie. Ustawienia określone na poziomie **armatury** mają wpływ na wszystkie eksploracje w ramach tej armatury. Ustawienia podrzędne &mdash; — Jeśli ustawienie jest zdefiniowane na poziomie **zestawu** i poziomów **armatury** , są używane ustawienia **armatury** .

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

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).
