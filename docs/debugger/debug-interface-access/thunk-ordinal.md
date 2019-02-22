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
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613274"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Określa typy thunk.

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
Standardowa THUNK_ORDINAL_NOTYPE thunk.

THUNK_ORDINAL_ADJUSTOR A `this` adjustor thunk.

Wirtualne THUNK_ORDINAL_VCALL thunk wywołania.

Thunk P-code THUNK_ORDINAL_PCODE.

Opóźnienie THUNK_ORDINAL_LOAD thunk obciążenia.

Przyrostowe THUNK_ORDINAL_TRAMP_INCREMENTAL thunk trampoline (trampoline sekcją thunk służy do Odbijanie wywołania z miejsca w pamięci z jednego do drugiego).

Thunk trampoline punktu THUNK_ORDINAL_TRAMP_BRANCHISLAND gałęzi.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane z wywołania [idiasymbol::get_thunkordinal —](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
