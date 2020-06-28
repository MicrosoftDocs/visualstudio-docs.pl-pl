---
title: 'IDiaSymbol:: get_hasLongJump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa43688b8fd3bb69cd8d44181da22924932e900
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463702"
---
# <a name="idiasymbolget_haslongjump"></a>IDiaSymbol::get_hasLongJump
Pobiera flagę, która określa, czy funkcja zawiera użycie polecenia [longjmp](/cpp/c-runtime-library/reference/longjmp) (sparowane z poleceniem [setjmp](/cpp/c-runtime-library/reference/setjmp) , takie jak Metoda stylu języka C dla obsługi wyjątków).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja zawiera `longjmp` polecenie; w przeciwnym razie zwraca `FALSE` .

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
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)