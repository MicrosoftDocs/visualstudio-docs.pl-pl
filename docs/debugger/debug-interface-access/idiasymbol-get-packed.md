---
title: 'IDiaSymbol:: get_packed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 420ba5b56342b4b1d5b8e4c2756aa828e5fe53b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739524"
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

określoną Zwraca `TRUE`, Jeśli UDT jest spakowany; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Spakowane oznacza, że wszystkie elementy członkowskie UDT są umieszczane jako blisko siebie jak to możliwe, bez dopełnienia pośredniego, aby wyrównać granice pamięci.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)