---
title: 'IDiaSymbol:: get_offset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6469180cada412fe5f08db1bd982f5a6e250e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853745"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
Pobiera przesunięcie lokalizacji symboli. Użyj, gdy [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) ma wartość `LocIsRegRel` lub `LocIsBitField` .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca przesunięcie w bajtach lokalizacji symboli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Przesunięcie pochodzi od określonego wcześniej znanego punktu. Na przykład przesunięcie dla `LocIsBitField` typu lokalizacji jest zwykle od początku klasy zawierającej.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)