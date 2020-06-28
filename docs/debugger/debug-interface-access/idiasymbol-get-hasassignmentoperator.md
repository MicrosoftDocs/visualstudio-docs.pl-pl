---
title: 'IDiaSymbol:: get_hasAssignmentOperator | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0d2410e8bb027aebf767970877870f1558a9c2b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463814"
---
# <a name="idiasymbolget_hasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
Pobiera flagę, która określa, czy typ danych zdefiniowany przez użytkownika ma zdefiniowane wszystkie operatory przypisania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasAssignmentOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy dla typu danych zdefiniowanego przez użytkownika istnieją zdefiniowane operatory przypisania; w przeciwnym razie zwraca wartość `FALSE` .

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