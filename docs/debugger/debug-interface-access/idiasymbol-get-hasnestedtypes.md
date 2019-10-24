---
title: 'IDiaSymbol:: get_hasNestedTypes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasNestedTypes method
ms.assetid: 1a8306bd-10dd-40a9-81fc-01f71c348484
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 315e009e264523b6f64deefa4a1b0367e262d034
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740476"
---
# <a name="idiasymbolget_hasnestedtypes"></a>IDiaSymbol::get_hasNestedTypes
Pobiera flagę, która określa, czy typ danych zdefiniowany przez użytkownika ma definicje typów zagnieżdżonych.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasNestedTypes ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE`, jeśli typ danych zdefiniowany przez użytkownika ma definicje typów zagnieżdżonych; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)