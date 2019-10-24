---
title: 'IDiaSymbol:: get_thunkOrdinal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bc8c523886d694ea413dedcf9a28e53e361882b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739136"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Pobiera typ thunk funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość z wyliczenia [THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) , która określa typ THUNK funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako wartość [wyliczenia symtagenum —](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk`.

 "Thunk" to fragment kodu, który konwertuje między 32-bitową przestrzenią adresową (znaną również jako płaska przestrzeń adresów) i 16-bitową przestrzenią adresową (znaną jako segmentowy obszar adresów).

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL, wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)