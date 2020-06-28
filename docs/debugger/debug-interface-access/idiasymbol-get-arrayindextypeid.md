---
title: 'IDiaSymbol:: get_arrayIndexTypeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexTypeId method
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4570585362da1475277f899bcb3c483d085918db
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464304"
---
# <a name="idiasymbolget_arrayindextypeid"></a>IDiaSymbol::get_arrayIndexTypeId
Pobiera identyfikator typu indeksu tablicy symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_arrayIndexTypeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca identyfikator typu indeksu tablicy symbolu.

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