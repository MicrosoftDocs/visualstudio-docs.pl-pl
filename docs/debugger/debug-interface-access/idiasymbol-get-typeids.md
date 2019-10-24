---
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739072"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Pobiera tablicę wartości identyfikatorów typu specyficznych dla kompilatora dla tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametry
 `cTypeIds`

podczas Rozmiar buforu do przechowywania danych.

 `pcTypeIds`

określoną Zwraca liczbę `typeIds` zapisanych lub, jeśli `typeIds` jest `NULL`, Łączna liczba dostępnych identyfikatorów typu.

 `typeIds[]`

określoną Tablica, która ma zostać wypełniona przy użyciu identyfikatorów typu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)