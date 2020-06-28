---
title: 'IDiaSymbol:: get_isAggregated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02e1a3a831ccd7394c58af4b744f0be8b905d763
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463485"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Pobiera flagę, która określa, czy symbol danych jest częścią agregacji lub kolekcji symboli; Kompilator traktuje zagregowane symbole jako osobne jednostki, ale są naprawdę częścią pojedynczego większego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy dane są częścią agregacji symboli, które dzielą się od symbolu nadrzędnego; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 [IDiaSymbol:: get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) Metoda jest `TRUE` dla symbolu, który jest elementem nadrzędnym symboli zagregowanych.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)