---
title: 'IDiaSymbol:: get_customCallingConvention | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_customCallingConvention method
ms.assetid: 0aa97951-f7e1-4fa5-a87f-2920460c122d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: df38f143eb3e0ab7fb7181b111c309e37e2ed4ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854375"
---
# <a name="idiasymbolget_customcallingconvention"></a>IDiaSymbol::get_customCallingConvention
Pobiera flagę, która określa, czy funkcja ma niestandardową konwencję wywoływania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_customCallingConvention(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma niestandardową konwencję wywoływania; w przeciwnym razie zwraca `FALSE` , funkcja ma znaną konwencję wywoływania.

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