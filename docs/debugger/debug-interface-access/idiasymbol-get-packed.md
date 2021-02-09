---
title: 'IDiaSymbol:: get_packed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2682086764294f9721153e9509088e653b9fd11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853710"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
Pobiera flagę, która określa, czy jest spakowany typ danych zdefiniowany przez użytkownika (UDT).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy typ UDT jest spakowany; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Spakowane oznacza, że wszystkie elementy członkowskie UDT są umieszczane jako blisko siebie jak to możliwe, bez dopełnienia pośredniego, aby wyrównać granice pamięci.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)