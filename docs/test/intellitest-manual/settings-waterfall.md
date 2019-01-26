---
title: Kaskadowy model ustawień | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5371900ec439a0d8c736d5437316705b6bfb98cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934520"
---
# <a name="settings-waterfall"></a>Kaskadowy model ustawień

Pojęcie kaskadowy model ustawień oznacza, że użytkownik może określić ustawienia na **zestawu**, **początkowych**, i **eksploracji** poziom:

* Zestaw - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Warunki początkowe - [PexClass](attribute-glossary.md#pexclass)
* Eksploracja - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone w **zestawu** poziom wpływają na wszystkie instalacje i eksploracji w ramach tego zestawu. Ustawienia określone w **początkowych** poziom mają wpływ na wszystkie eksploracji w ramach tego początkowych. Podrzędne ustawień win&mdash;Jeśli to ustawienie jest zdefiniowany na **zestawu** i **początkowych** poziomy **początkowych** ustawienia są używane.

Należy zauważyć, że niektóre ustawienia specyficzne dla **zestawu** poziom lub **początkowych** poziom.

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

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).