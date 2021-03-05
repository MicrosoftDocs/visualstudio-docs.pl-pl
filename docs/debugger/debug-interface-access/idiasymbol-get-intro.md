---
description: Pobiera flagę, która określa, czy funkcja jest wprowadzeniem do funkcji wirtualnej.
title: 'IDiaSymbol:: get_intro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad2e791995f4edc1b09655640bc339d577f7f37d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160877"
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

określoną Zwraca `TRUE` czy funkcja jest wprowadzająca wartość wirtualną; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="example"></a>Przykład

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Obie `A::f1` `B::f1` funkcje i są funkcjami wirtualnymi, ale to wprowadzenie do usługi Virtual `A::f1` Machines.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
