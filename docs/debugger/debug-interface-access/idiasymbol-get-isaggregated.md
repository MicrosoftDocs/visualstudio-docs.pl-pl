---
description: Pobiera flagę, która określa, czy symbol danych jest częścią agregacji lub kolekcji symboli; Kompilator traktuje zagregowane symbole jako osobne jednostki, ale są naprawdę częścią pojedynczego większego symbolu.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e78ec7f180ad1c719d562975377a413156bb1480
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160863"
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
