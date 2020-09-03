---
title: Set podstawy — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665421"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia lub zwraca wartość numeryczną używaną do wyświetlania wartości całkowitych.

## <a name="syntax"></a>Składnia

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
 `10` lub `16` lub `hex` `dec` opcjonalnie. Wskazuje liczbę dziesiętną (10 lub gru) lub szesnastkową (16 lub szesnastkową). Jeśli argument jest pominięty, zostanie zwrócona bieżąca wartość podstawy.

## <a name="example"></a>Przykład
 W tym przykładzie ustawiono środowisko do wyświetlania wartości całkowitych w formacie szesnastkowym.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
