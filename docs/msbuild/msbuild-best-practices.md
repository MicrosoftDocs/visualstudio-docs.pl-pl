---
title: MsBuild Najlepsze praktyki | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263152"
---
# <a name="msbuild-best-practices"></a>MSBuild najlepsze rozwiązania

Zaleca się następujące najlepsze rozwiązania dotyczące pisania skryptów MSBuild:

- Domyślne wartości właściwości najlepiej obsługiwać przy użyciu atrybutu, `Condition` a nie przez deklarowanie właściwości, której wartość domyślna może zostać zastąpiona w wierszu polecenia. Na przykład, użyj

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Ogólnie rzecz biorąc, należy unikać używania symboli wieloznacznych podczas wybierania elementów. Zamiast tego należy określić pliki jawnie. Dzieje się tak, ponieważ w większości typów projektów MSBuild rozszerza symbole wieloznaczne w różnym czasie, na przykład podczas dodawania lub usuwania elementów, co może prowadzić do nieoczekiwanego zachowania. Wyjątek od tego jest w .NET Core SDK stylu projektów, które przetwarzają symbole wieloznaczne poprawnie.

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
