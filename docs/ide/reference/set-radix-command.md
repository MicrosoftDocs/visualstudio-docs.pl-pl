---
title: Ustaw Radix — Polecenie
description: Dowiedz się więcej o poleceniu Set podstawy i sposobie jego ustawiania lub zwraca wartość numeryczną używaną do wyświetlania wartości całkowitych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957689"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
Ustawia lub zwraca wartość numeryczną używaną do wyświetlania wartości całkowitych.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
`10`lub `16` lub `hex``dec`

Opcjonalny. Wskazuje liczbę dziesiętną (10 lub gru) lub szesnastkową (16 lub szesnastkową). Jeśli argument jest pominięty, zostanie zwrócona bieżąca wartość podstawy.

## <a name="example"></a>Przykład
W tym przykładzie ustawiono środowisko do wyświetlania wartości całkowitych w formacie szesnastkowym.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)