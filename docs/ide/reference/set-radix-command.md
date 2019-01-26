---
title: Ustaw Radix — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c7533f9ec4dd9a915d50aa7676dcf6397ec451
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924100"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
Ustawia lub zwraca base numeryczne, używany do wyświetlania wartości całkowitych.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
 `10` lub `16` lub `hex` lub `dec`

 Opcjonalna. Wskazuje dziesiętne (10 lub gru) lub liczba szesnastkowa (16 lub szesnastkowych). Jeśli argument jest pominięty, zwracany jest bieżąca wartość podstawy.

## <a name="example"></a>Przykład
 W tym przykładzie środowiska, aby wyświetlić wartości całkowite w formacie szesnastkowym.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)