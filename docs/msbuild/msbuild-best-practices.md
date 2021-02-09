---
title: Najlepsze rozwiązania dla programu MSBuild | Microsoft Docs
description: Dowiedz się więcej o najlepszych rozwiązaniach dotyczących pisania skryptów programu MSBuild, takich jak używanie atrybutów warunku i używanie symboli wieloznacznych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919192"
---
# <a name="msbuild-best-practices"></a>Najlepsze rozwiązania w programie MSBuild

Zalecamy stosowanie następujących najlepszych rozwiązań dotyczących pisania skryptów programu MSBuild:

- Domyślne wartości właściwości są najlepiej obsługiwane przy użyciu `Condition` atrybutu, a nie poprzez deklarowanie właściwości, której wartość domyślna może zostać przesłonięta w wierszu polecenia. Na przykład użyj

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Ogólnie rzecz biorąc, Unikaj używania symboli wieloznacznych podczas zaznaczania elementów. Zamiast tego należy jawnie określić pliki. Jest to spowodowane tym, że w większości typów projektów MSBuild rozszerza symbole wieloznaczne w różnych godzinach, na przykład podczas dodawania lub usuwania elementów, co może prowadzić do nieoczekiwanego zachowania. Wyjątkiem jest w projektach w stylu zestaw .NET Core SDK, które poprawnie przetwarzają symbole wieloznaczne.

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
