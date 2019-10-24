---
title: Ustaw Radix — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f920311301b722c11bea4a9f4eb90e9aa7663d80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747736"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
Ustawia lub zwraca wartość numeryczną używaną do wyświetlania wartości całkowitych.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
`10` lub `16` lub `hex` lub `dec`

Opcjonalny. Wskazuje liczbę dziesiętną (10 lub gru) lub szesnastkową (16 lub szesnastkową). Jeśli argument jest pominięty, zostanie zwrócona bieżąca wartość podstawy.

## <a name="example"></a>Przykład
W tym przykładzie ustawiono środowisko do wyświetlania wartości całkowitych w formacie szesnastkowym.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)