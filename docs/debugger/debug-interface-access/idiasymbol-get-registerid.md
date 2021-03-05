---
description: Pobiera oznaczenie rejestru lokalizacji, gdy element LocationType Enumeration ma wartość LocIsEnregistered '.
title: 'IDiaSymbol:: get_registerId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f6845c83b46fb524221933eb859742ebe7a95e6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161901"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Pobiera oznaczenie rejestru dla lokalizacji, gdy [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsEnregistered` .

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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Jeśli symbol jest powiązany z rejestrem, czyli jeśli [Wyliczenie typu LocationType](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsRegRel` , użyj `get_registerId` metody, a po niej wywołanie metody [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) , aby uzyskać przesunięcie z rejestru, w którym znajduje się symbol.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
