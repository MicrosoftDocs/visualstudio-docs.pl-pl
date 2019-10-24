---
title: 'IDiaSymbol:: get_constType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_constType method
ms.assetid: cb43605e-fa39-4f83-b047-f936a8019d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12e811fe67fc9a990052737882463ac341ef34b2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740782"
---
# <a name="idiasymbolget_consttype"></a>IDiaSymbol::get_constType
Pobiera flagę, która określa, czy typem danych zdefiniowanym przez użytkownika jest stała.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_constType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE`, jeśli typ danych zdefiniowany przez użytkownika to stała; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)