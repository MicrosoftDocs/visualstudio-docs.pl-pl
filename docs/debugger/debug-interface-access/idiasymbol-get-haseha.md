---
title: 'IDiaSymbol:: get_hasEHa | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc96412402202f0e6e20c85778f14b6be444d9bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863383"
---
# <a name="idiasymbolget_haseha"></a>IDiaSymbol::get_hasEHa
Pobiera flagę, która określa, czy funkcja zawiera asynchroniczną (strukturalną) obsługę wyjątków.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasEHa(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma jakikolwiek asynchroniczny sposób obsługi wyjątków; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Możliwe jest mieszanie asynchronicznej lub strukturalnej obsługi wyjątków z obsługą wyjątków w stylu języka C++, ale wymaga określonego przełącznika kompilatora,/EHa, aby go włączyć.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)