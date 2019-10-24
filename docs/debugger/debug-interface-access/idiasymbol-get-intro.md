---
title: 'IDiaSymbol:: get_intro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740349"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Pobiera flagę, która określa, czy funkcja jest wprowadzeniem do funkcji wirtualnej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

określoną Zwraca `TRUE`, jeśli funkcja jest wprowadzeniem wirtualnym; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="example"></a>Przykład

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Zarówno `A::f1`, jak i `B::f1` są funkcjami wirtualnymi, ale `A::f1` jest wprowadzeniem wirtualnym.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
