---
description: Pobiera bajty danych symbolu producenta OEM.
title: 'IDiaSymbol:: get_dataBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09156b8d99daa5cbfd065110073c3c185c3ac0a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161017"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
Pobiera bajty danych symbolu producenta OEM.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

podczas Rozmiar buforu do przechowywania danych.

 `pcbData`

określoną Zwraca liczbę bajtów zapisanych lub, jeśli `data` parametr ma `NULL` wartość, zwraca liczbę dostępnych bajtów.

 `data[]`
- [out,] Bufor wypełniony bajtami danych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
