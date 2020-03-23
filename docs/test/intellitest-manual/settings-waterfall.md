---
title: Ustawienia wodospadu | Narzędzie testowe Microsoft IntelliTest Developer
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591583"
---
# <a name="settings-waterfall"></a>Kaskadowy model ustawień

Koncepcja wodospadu ustawień oznacza, że użytkownik może określić ustawienia na poziomie **Zestawu,** **Oprawa**i **Eksploracja:**

* Montaż - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Oprawa - [PexClass](attribute-glossary.md#pexclass)
* Eksploracja - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone na poziomie **złożenia** mają wpływ na wszystkie umocowania i eksploracji w ramach tego zestawu. Ustawienia określone na poziomie **urządzenia** wpływają na wszystkie eksploracje w ramach tego urządzenia. Ustawienia podrzędne&mdash;wygrywają, jeśli ustawienie jest zdefiniowane na poziomach **złożenia** i **umocowania,** używane są ustawienia **terminowania.**

Należy zauważyć, że niektóre ustawienia są specyficzne dla poziomu **złożenia** lub **poziom umocowania.**

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

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
