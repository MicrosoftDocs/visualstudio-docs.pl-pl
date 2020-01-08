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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592090"
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

## <a name="see-also"></a>Zobacz także
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
