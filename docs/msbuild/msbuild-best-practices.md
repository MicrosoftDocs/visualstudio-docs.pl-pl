---
title: Najlepsze rozwiązania dla programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3605109519dccaafa1367464bd8c2385df5e93e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633424"
---
# <a name="msbuild-best-practices"></a>Najlepsze rozwiązania dla programu MSBuild

Zalecamy stosowanie następujących najlepszych rozwiązań dotyczących pisania skryptów programu MSBuild:

- Domyślne wartości właściwości są najlepiej obsługiwane przy użyciu atrybutu `Condition`, a nie poprzez deklarowanie właściwości, której wartość domyślna może zostać przesłonięta w wierszu polecenia. Na przykład użyj

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Unikaj symboli wieloznacznych podczas zaznaczania elementów. Zamiast tego należy jawnie określić pliki. Ułatwia to śledzenie błędów, które mogą wystąpić podczas dodawania lub usuwania plików.

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
