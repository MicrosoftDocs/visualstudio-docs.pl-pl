---
title: 'IDiaSymbol:: get_slot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cb7c89828bb4b0715f97aaba37fd335c8f1eb6c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853605"
---
# <a name="idiasymbolget_slot"></a>IDiaSymbol::get_slot
Pobiera numer gniazda lokalizacji. Użyj, gdy jest [wyliczana wartość LocationType](../../debugger/debug-interface-access/locationtype.md) `LocIsSlot` .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_slot ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer gniazda lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)