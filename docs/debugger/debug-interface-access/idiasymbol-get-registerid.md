---
title: 'IDiaSymbol:: get_registerId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739467"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Pobiera oznaczenie rejestru dla lokalizacji, gdy [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) ma wartość `LocIsEnregistered`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca oznaczenie rejestru lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Jeśli symbol jest powiązany z rejestrem, czyli jeśli [Wyliczenie elementu LocationType](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsRegRel`, użyj metody `get_registerId`, po której następuje wywołanie metody [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) , aby uzyskać przesunięcie z rejestru, w którym symbol jest znajduje.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)