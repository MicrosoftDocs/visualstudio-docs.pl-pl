---
description: Pobiera flagę wskazującą, czy sekcja nie powinna być uzupełniona do następnej granicy pamięci.
title: 'IDiaSectionContrib:: get_nopad | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 48bbfdbd14cd7f2d00a9c0ba4530c78fed62141d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157211"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
Pobiera flagę wskazującą, czy sekcja nie powinna być uzupełniona do następnej granicy pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy sekcja nie powinna być uzupełniona do następnej granicy pamięci; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jest to właściwość zwykle widoczna tylko dla starszych plików.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
