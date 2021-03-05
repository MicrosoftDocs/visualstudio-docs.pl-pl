---
description: Pobiera flagę, która określa, czy funkcja zawiera wszelką obsługę wyjątków strukturalnych (C/C++)) (na przykład bloki _try/__except).
title: 'IDiaSymbol:: get_hasSEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a802a14c1c4e9b9c3b080c751d8cd512c3adf75d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156267"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Pobiera flagę, która określa, czy funkcja zawiera wszelką [obsługę wyjątków strukturalnych (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (na przykład bloki __try/ \_ _Except).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma bloki obsługi wyjątków strukturalnych; w przeciwnym razie zwraca `FALSE` .

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
- [Obsługa wyjątków strukturalnych (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)
