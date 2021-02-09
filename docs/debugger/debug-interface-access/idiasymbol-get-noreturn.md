---
title: 'IDiaSymbol:: get_noReturn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 631cb2f9e6ebc9d0e88816bb862bf2c5429c7428
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853822"
---
# <a name="idiasymbolget_noreturn"></a>IDiaSymbol::get_noReturn
Pobiera flagę, która określa, czy funkcja została oznaczona jako nigdy zwracająca atrybut [noreturn](/cpp/cpp/noreturn) .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_noReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 pFlag

określoną Zwraca `TRUE` czy funkcja została zadeklarowana jako nigdy zwracająca `noreturn` atrybut; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [noreturn](/cpp/cpp/noreturn)