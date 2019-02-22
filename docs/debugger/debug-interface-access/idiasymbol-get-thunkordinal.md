---
title: Idiasymbol::get_thunkordinal — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 78ce8311e9504261399f22feefebb93fb9b3c64f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605955"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Pobiera typ thunk funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca wartość z zakresu od [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md) wyliczenie, który określa typ thunk funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartość `SymTagThunk`.

 "thunk" jest fragmentem kodu, który wykonuje konwersję między pamięci 32-bitowej przestrzeni adresowej (znany także jako płaska przestrzeń adresowa) i 16-bitowej przestrzeni adresowej (znanych jako przestrzeń adresową segmenty).

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL, wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)