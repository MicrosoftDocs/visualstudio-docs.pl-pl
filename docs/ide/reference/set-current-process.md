---
title: Ustaw bieżący proces
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3440c66d79fef3eac3744681870c9ce1ed0e97b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593554"
---
# <a name="set-current-process"></a>Ustaw bieżący proces
Ustawia określony proces jako aktywny proces w debugerze.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
`index`

Wymagany. Indeks procesu.

## <a name="remarks"></a>Uwagi
Podczas debugowania można dołączyć do wielu procesów, ale tylko jeden proces jest aktywny w programie w danym momencie. Możesz użyć `SetCurrentProcess` polecenie, aby ustawić aktywny proces.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
