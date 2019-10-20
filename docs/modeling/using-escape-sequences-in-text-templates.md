---
title: Korzystanie z sekwencji unikowych w szablonach tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662916"
---
# <a name="use-escape-sequences-in-text-templates"></a>Korzystanie z sekwencji ucieczki w szablonach tekstowych

Za pomocą sekwencji unikowych w szablonach tekstowych można generować Tagi szablonu tekstu i ( C# tylko w kodzie) do ucieczki znaków kontrolnych i cudzysłowów.

Aby wydrukować otwarte i zamykające Tagi dla standardowego bloku kodu do pliku wyjściowego, należy wprowadzić znaczniki w następujący sposób:

```
\<# ... \#>
```

Można to zrobić z innymi dyrektywami szablonu tekstu i tagami bloków kodu.

Jeśli blok tekstu zawiera ciągi używane do ucieczki tagów szablonu tekstu, można użyć następujących sekwencji unikowych:

- Jeśli tag szablonu tekstu jest poprzedzony parzystą liczbą znaków ucieczki (\\), Analizator szablonu będzie zawierał połowę znaków ucieczki i dołączył sekwencję jako tag szablonu tekstu. Na przykład jeśli w szablonie tekstowym istnieją cztery znaki ucieczki, w wygenerowanym pliku będą znajdować się dwa znaki "\\".

- Jeśli tag szablonu tekstu jest poprzedzony nieparzystą liczbą znaków ucieczki (\\), Analizator szablonu będzie zawierał połowę znaków "\\" i sam tag (\< # lub # >). Tag nie jest traktowany jako tag szablonu tekstu.

- Jeśli znak ucieczki (\\) pojawia się w dowolnym miejscu w dowolnej innej kolejności niż w przypadku ucieczki znaku kontrolnego lub cudzysłowu C# (tylko w przypadku), znak będzie wyprowadzany bezpośrednio.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)