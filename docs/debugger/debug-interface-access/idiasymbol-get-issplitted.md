---
title: 'IDiaSymbol:: get_isSplitted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbdeb9b4a5bf6f173cbb2a0bd593202317d62342
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853997"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Pobiera flagę, która określa, czy symbol danych został podzielony na agregację, czy do kolekcji innych symboli; Kompilator traktuje symbole jako osobne jednostki, nawet jeśli są naprawdę częścią większego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy symbol został podzielony na agregację symboli; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Metoda [IDiaSymbol:: get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) zwraca `TRUE` dla wszystkich symboli, które są częścią symbolu podziału.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)