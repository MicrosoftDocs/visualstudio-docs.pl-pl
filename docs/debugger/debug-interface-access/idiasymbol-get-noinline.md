---
title: 'IDiaSymbol:: get_noInline | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noInline method
ms.assetid: 5c610b78-f1a3-494a-acf8-c42b97935be1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3ac08460995cbaec149c5dda9ffc4c1e3e5bfbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862963"
---
# <a name="idiasymbolget_noinline"></a>IDiaSymbol::get_noInline
Pobiera flagę, która określa, czy funkcja została oznaczona jako niewbudowana (przy użyciu atrybutu [NoLine](/cpp/cpp/noinline) ).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_noInline(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma `noinline` atrybut; w przeciwnym razie zwraca `FALSE` .

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
- [noinline](/cpp/cpp/noinline)