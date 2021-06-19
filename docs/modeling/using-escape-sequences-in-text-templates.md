---
title: Korzystanie z sekwencji unikowych w szablonach tekstowych
description: Dowiedz się, jak używać sekwencji ucieczki w szablonach tekstowych do generowania tagów szablonu tekstu oraz do ucieczki znaków kontrolnych i cudzysłowów tylko w kodzie C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a3cdabd38f2bf4ef38a31807fabed3ac837b26b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388454"
---
# <a name="use-escape-sequences-in-text-templates"></a>Używanie sekwencji ucieczki w szablonach tekstowych

Sekwencji ucieczki w szablonach tekstowych można używać do generowania tagów szablonu tekstu i (tylko w kodzie C#) w celu ucieczki przed znakami kontrolnymi i cudzysłowami.

Aby wydrukować tagi otwierania i zamykania standardowego bloku kodu do pliku wyjściowego, należy w następujący sposób wymykać tagi ucieczki:

```
\<# ... \#>
```

To samo można zrobić z innymi dyrektywami szablonu tekstowego i tagami bloku kodu.

Jeśli blok tekstu zawiera ciągi używane do ucieczki tagów szablonu tekstu, można użyć następujących sekwencji ucieczki:

- Jeśli tag szablonu tekstu jest poprzedzony parzystą liczbą znaków ucieczki ( ), parser szablonu będzie zawierać połowę znaków ucieczki i dołącza sekwencję jako tag \\ szablonu tekstu. Jeśli na przykład szablon tekstowy zawiera cztery znaki ucieczki, wygenerowany plik będzie zawierał dwa znaki \\ "".

- Jeśli tag szablonu tekstu jest poprzedzony nieparzystą liczbą znaków ucieczki ( ), parser szablonu będzie zawierać połowę \\ znaków " " oraz sam tag ( \\ \<# or #> ). Tag nie jest traktowany jako tag szablonu tekstu.

- Jeśli znak ucieczki ( ) pojawia się w dowolnym miejscu w dowolnej sekwencji innej niż, gdzie unika znaku kontrolnego lub cudzysłowu (tylko w języku C#), znak będzie bezpośrednio \\ wyjściowy.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
