---
title: 'IDiaSymbol:: get_classParentId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParentId method
ms.assetid: f11e3ccb-215d-418c-b8c3-e63159234915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a965d04bf6cd41bcd19c2b5e987f610149f601c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854487"
---
# <a name="idiasymbolget_classparentid"></a>IDiaSymbol::get_classParentId
Pobiera nadrzędny identyfikator klasy symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_classParentId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca identyfikator klasy nadrzędnej symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Identyfikator jest unikatową wartością utworzoną przez DIA SDK, aby oznaczyć wszystkie symbole jako unikatowe.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)