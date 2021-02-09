---
title: 'IDiaSymbol:: get_isMSILNetmodule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943f496ff4c08a6f3b2047c977c4ed4588190587
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863159"
---
# <a name="idiasymbolget_ismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
Pobiera flagę wskazującą, czy moduł jest modułem. (w języku pośrednim firmy Microsoft), który zawiera tylko metadane i bez symboli natywnych.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isMSILNetmodule(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy moduł jest MSIL; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest dostępna w `SymTagCompilandDetails` typie symbolu (zobacz [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)