---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738494"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Wyznacza typy thunk.

## <a name="syntax"></a>Składnia

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Elementy
THUNK_ORDINAL_NOTYPE standardowa THUNK.

THUNK_ORDINAL_ADJUSTOR `this` THUNK.

THUNK_ORDINAL_VCALL wirtualne wywołania THUNK.

THUNK_ORDINAL_PCODE P-Code THUNK.

THUNK_ORDINAL_LOAD Opóźnij obciążenie THUNK.

THUNK_ORDINAL_TRAMP_INCREMENTAL przyrostowe Trampoline THUNK (Trampoline THUNK jest używany do odbijania wywołań z jednego miejsca w pamięci do innej).

THUNK_ORDINAL_TRAMP_BRANCHISLAND Trampoline THUNK.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane z wywołania metody [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
