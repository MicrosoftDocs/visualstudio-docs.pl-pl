---
title: 'IDiaSymbol:: get_hasEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d387d37103773e7352357ebef5f9134bcff85c59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854249"
---
# <a name="idiasymbolget_haseh"></a>IDiaSymbol::get_hasEH
Pobiera flagę, która określa, czy funkcja zawiera niezarządzaną obsługę wyjątków w stylu C++ (na przykład blok try/catch).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma jakąkolwiek obsługę wyjątków w stylu C++; w przeciwnym razie zwraca `FALSE` .

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