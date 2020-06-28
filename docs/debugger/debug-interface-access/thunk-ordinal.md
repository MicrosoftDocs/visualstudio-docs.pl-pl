---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d2fe7c62ce04e61a8476731ed14ee14f60e2b044
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461043"
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
THUNK_ORDINAL_NOTYPE Standard THUNK.

THUNK_ORDINAL_ADJUSTOR `this` THUNK.

THUNK_ORDINAL_VCALL THUNK wywołania wirtualnego.

THUNK_ORDINAL_PCODE P-Code THUNK.

THUNK_ORDINAL_LOAD Opóźnij obciążenie THUNK.

THUNK_ORDINAL_TRAMP_INCREMENTAL przyrostowe Trampoline THUNK (Trampoline THUNK służy do odbijania wywołań z jednego miejsca w pamięci do innej).

THUNK_ORDINAL_TRAMP_BRANCHISLAND rozgałęzienie THUNK Trampoline.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane z wywołania metody [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
