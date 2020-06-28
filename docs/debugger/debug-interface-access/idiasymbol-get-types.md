---
title: 'IDiaSymbol:: get_types | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d947eed08ba28cfdd68e2cd7d34998412fc8bc3a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461686"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Pobiera tablicę typów specyficznych dla kompilatora dla tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parametry
 `cTypes`

podczas Rozmiar buforu do przechowywania danych.

 `pcTypes`

określoną Zwraca liczbę typów zapisanych lub, jeśli `types` parametr ma wartość `NULL` , całkowitą liczbę dostępnych typów.

 `types[]`

określoną Tablica, która ma zostać wypełniona obiektami [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , które reprezentują wszystkie typy dla tego symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)