---
title: 'IDiaSymbol:: get_volatileType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c7aefecceaa7ed67c262360ca8b6b7bfba08e0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853332"
---
# <a name="idiasymbolget_volatiletype"></a>IDiaSymbol::get_volatileType
Pobiera flagę, która określa, czy typ danych zdefiniowany przez użytkownika (UDT) jest nietrwały.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy typ UDT jest nietrwały; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 W języku C++, można oznaczyć przy użyciu `volatile` słowa kluczowego UDT, wskazując, że jego zawartość nie może być założono, że istnieje z jednego dostępu do następnego.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)