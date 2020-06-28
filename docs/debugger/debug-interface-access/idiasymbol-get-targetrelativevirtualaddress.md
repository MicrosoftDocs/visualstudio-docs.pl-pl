---
title: 'IDiaSymbol:: get_targetRelativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6648be961999e5eaf156f2c4b0dea511aed4eb59
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461852"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Pobiera względny adres wirtualny (RVA) elementu docelowego thunk.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca RVA elementu docelowego thunk.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako wartość [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` .

 "Thunk" to fragment kodu, który konwertuje między 32-bitową przestrzenią adresową (znaną również jako płaska przestrzeń adresów) i 16-bitową przestrzenią adresową (znaną jako segmentowy obszar adresów).

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)