---
description: Pobiera liczbę bitów lub bajtów pamięci używanej przez obiekt reprezentowany przez ten symbol.
title: 'IDiaSymbol:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a7b3a7a88c688f8ff68f2c1280390f10110c3a9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162013"
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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Jeśli [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) symbolu ma wartość `LocIsBitField` , Długość zwrócona przez tę metodę jest w bitach; w przeciwnym razie długość jest wyrażona w bajtach dla wszystkich innych typów lokalizacji.

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

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
