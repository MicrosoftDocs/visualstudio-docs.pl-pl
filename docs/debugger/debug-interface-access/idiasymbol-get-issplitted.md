---
title: IDiaSymbol::get_isSplitted | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee91134997dad5f5361de6b07af1a99dfc420f5e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401247"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
Pobiera flagę określającą, czy symbol danych został podzielony na agregacji lub kolekcji innych symboli; Kompilator traktuje jako osobne jednostki, symbole, nawet jeśli są one naprawdę częścią symbol większe.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

[out] Zwraca `TRUE` Jeśli symbol został podzielony na agregację symboli; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 [Idiasymbol::get_isaggregated —](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) metoda zwraca `TRUE` dla wszystkich symboli, które należą do podziału symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|DIA SDK w wersji 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)