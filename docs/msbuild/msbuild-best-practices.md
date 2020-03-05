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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263152"
---
# <a name="msbuild-best-practices"></a>Najlepsze rozwiązania w programie MSBuild

Zalecamy stosowanie następujących najlepszych rozwiązań dotyczących pisania skryptów programu MSBuild:

- Domyślne wartości właściwości są najlepiej obsługiwane przy użyciu atrybutu `Condition`, a nie poprzez deklarowanie właściwości, której wartość domyślna może zostać przesłonięta w wierszu polecenia. Na przykład użyj

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Ogólnie rzecz biorąc, Unikaj używania symboli wieloznacznych podczas zaznaczania elementów. Zamiast tego należy jawnie określić pliki. Jest to spowodowane tym, że w większości typów projektów MSBuild rozszerza symbole wieloznaczne w różnych godzinach, na przykład podczas dodawania lub usuwania elementów, co może prowadzić do nieoczekiwanego zachowania. Wyjątkiem jest w projektach w stylu zestaw .NET Core SDK, które poprawnie przetwarzają symbole wieloznaczne.

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
