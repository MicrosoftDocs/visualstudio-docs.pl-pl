---
title: Kaskadowy model ustawień | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 27eb9b7e3cda7c05515f5a7413b067dce2b8567e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000403"
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