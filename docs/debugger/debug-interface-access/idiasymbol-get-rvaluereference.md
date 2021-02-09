---
title: 'IDiaSymbol:: get_RValueReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_RValueReference method
ms.assetid: c6c8c543-253e-4c23-a939-3e66f3db0ee2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a66ec650c1e12e795241ab31cafc50ebaacf20ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853654"
---
# <a name="idiasymbolget_rvaluereference"></a>IDiaSymbol::get_RValueReference
Pobiera flagę, która określa, czy typ wskaźnika to odwołanie rvalue. Użyj, gdy [Wyliczenie SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) jest ustawione na typ wskaźnika.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_RValueReference (
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy wskaźnik jest odwołaniem rvalue; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)