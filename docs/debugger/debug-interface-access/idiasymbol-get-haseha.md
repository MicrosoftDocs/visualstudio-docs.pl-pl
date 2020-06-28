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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c565a8c13b31feb78c8d60bf0b18bbc923f14f5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463751"
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