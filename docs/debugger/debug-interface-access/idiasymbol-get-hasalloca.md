---
title: 'IDiaSymbol:: get_hasAlloca | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b6dfbb3d12e01656117c0b1a3391af5a0578358
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854291"
---
# <a name="idiasymbolget_hasalloca"></a>IDiaSymbol::get_hasAlloca
Pobiera flagę, która określa, czy funkcja zawiera wywołanie `alloca` (które jest używane do przydzielania pamięci na stosie).

## <a name="syntax"></a>Składnia

```cpp
HRESULT get_hasAlloca(   BOOL *pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja zawiera wywołanie `alloca` ; w przeciwnym razie zwraca `FALSE` .

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