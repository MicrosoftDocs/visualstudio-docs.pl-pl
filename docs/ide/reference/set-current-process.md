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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
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
Można dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w dubberze w danym momencie. Za pomocą `SetCurrentProcess` polecenia można ustawić aktywny proces.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
