---
title: 'IDiaSymbol:: get_bitPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_bitPosition method
ms.assetid: b0059407-8655-497b-81ca-025595989371
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2c0c796bc01b6829e3345c45080f9ea2215d235
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854494"
---
# <a name="idiasymbolget_bitposition"></a>IDiaSymbol::get_bitPosition
Pobiera bitową pozycję lokalizacji. Używany, gdy jest [wyliczana wartość LocationType](../../debugger/debug-interface-access/locationtype.md) `LocIsBitField` .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_bitPosition ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca pozycję bitu lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)