---
title: 'IDiaSymbol:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114d9f7b00bbe5d322e7b6893e96fbbabec9d002
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739980"
---
# <a name="idiasymbolget_length"></a>IDiaSymbol::get_length
Pobiera liczbę bitów lub bajtów pamięci używanej przez obiekt reprezentowany przez ten symbol.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów lub bitów pamięci używanej przez obiekt reprezentowany przez ten symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Jeśli [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) symbolu ma `LocIsBitField`, Długość zwrócona przez tę metodę jest w bitach; w przeciwnym razie długość jest wyrażona w bajtach dla wszystkich innych typów lokalizacji.

## <a name="example"></a>Przykład

```C++
IDiaSymbol* pSymbol;
ULONGLONG   length;
pSymbol->get_length( &length );
```

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)