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
ms.openlocfilehash: 24f4c08147f72168f5207418a51d7a9cfa8a2b51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934554"
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