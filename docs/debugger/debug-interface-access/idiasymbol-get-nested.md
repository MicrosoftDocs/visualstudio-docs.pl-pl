---
title: 'IDiaSymbol:: get_nested | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_nested method
ms.assetid: 6ae46d43-8486-48d6-a6f2-d73ebf4023e3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04de0500105a460006d49788c5563eba3820685f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853836"
---
# <a name="idiasymbolget_nested"></a>IDiaSymbol::get_nested
Pobiera flagę, która określa, czy typ danych zdefiniowany przez użytkownika jest zagnieżdżony.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_nested ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy typ danych zdefiniowany przez użytkownika jest zagnieżdżony; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)