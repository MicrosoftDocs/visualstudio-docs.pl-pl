---
title: Idiasymbol::get_intro — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 020d631405586227d91fd06fb1794ab5554d1075
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226913"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
Pobiera flagę określającą, czy funkcja jest wprowadzenie do funkcji wirtualnej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`  
[out] Zwraca `TRUE` Jeśli funkcja jest wprowadzenie wirtualnych; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="example"></a>Przykład

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Zarówno `A::f1` i `B::f1` funkcji wirtualnych, ale `A::f1` jest wprowadzenie wirtualny.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
