---
title: Ustaw bieżący proces
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855286"
---
# <a name="set-current-process"></a>Ustaw bieżący proces
Ustawia określony proces jako aktywny procesu w debugerze.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
 `index`

 Wymagana. Indeks procesu.

## <a name="remarks"></a>Uwagi
 Podczas debugowania, ale tylko jeden proces jest aktywny w programie do usuwania błędów w dowolnym momencie można dołączyć do wielu procesów. Możesz użyć `SetCurrentProcess` polecenie, aby ustawić aktywny proces.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)