---
title: Korzystanie z sekwencji unikowych w szablonach tekstowych
description: Dowiedz się, jak używać sekwencji unikowych w szablonach tekstowych do generowania tagów szablonu tekstu oraz do ucieczki znaków kontrolnych i cudzysłowów w kodzie C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924337"
---
# <a name="use-escape-sequences-in-text-templates"></a>Korzystanie z sekwencji ucieczki w szablonach tekstowych

Za pomocą sekwencji unikowych w szablonach tekstowych można generować Tagi szablonu tekstu i (tylko w kodzie C#) do ucieczki znaków kontrolnych i cudzysłowów.

Aby wydrukować otwarte i zamykające Tagi dla standardowego bloku kodu do pliku wyjściowego, należy wprowadzić znaczniki w następujący sposób:

```
\<# ... \#>
```

Można to zrobić z innymi dyrektywami szablonu tekstu i tagami bloków kodu.

Jeśli blok tekstu zawiera ciągi używane do ucieczki tagów szablonu tekstu, można użyć następujących sekwencji unikowych:

- Jeśli tag szablonu tekstu jest poprzedzony parzystą liczbą znaków ucieczki ( \\ ), Analizator szablonu będzie zawierał połowę znaków ucieczki i dołączył sekwencję jako tag szablonu tekstu. Na przykład jeśli w szablonie tekstu znajdują się cztery znaki ucieczki, w wygenerowanym pliku będą się znajdować dwa \\ znaki.

- Jeśli tag szablonu tekstu jest poprzedzony przez nieparzystą liczbę znaków ucieczki ( \\ ), Analizator szablonu będzie zawierał połowę \\ znaków "" i sam tag ( \<# or #> ). Tag nie jest traktowany jako tag szablonu tekstu.

- Jeśli znak ucieczki ( \\ ) pojawia się w dowolnym miejscu w dowolnej innej kolejności niż w przypadku ucieczki znaku kontrolnego lub cudzysłowu (tylko w języku C#), znak będzie wyprowadzany bezpośrednio.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
