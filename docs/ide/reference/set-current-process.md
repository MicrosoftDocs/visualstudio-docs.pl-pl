---
title: Ustaw bieżący proces
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8d4c23934ddb6a838344eb6252f6002a5ecf10d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926091"
---
# <a name="set-current-process"></a>Ustaw bieżący proces
Ustawia określony proces jako aktywny proces w debugerze.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
`index`

Wymagane. Indeks procesu.

## <a name="remarks"></a>Uwagi
Podczas debugowania można dołączyć do wielu procesów, ale tylko jeden proces jest aktywny w programie w danym momencie. Możesz użyć `SetCurrentProcess` polecenia, aby ustawić aktywny proces.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)