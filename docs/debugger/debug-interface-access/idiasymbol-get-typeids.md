---
description: Pobiera tablicę wartości identyfikatorów typu specyficznych dla kompilatora dla tego symbolu.
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04a39af21ebb8a409656bd8b8ae0b4323da33c60
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155615"
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

określoną Zwraca liczbę `typeIds` zapisów lub, jeśli `typeIds` jest `NULL` , a następnie łączną liczbę dostępnych identyfikatorów typu.

 `typeIds[]`

określoną Tablica, która ma zostać wypełniona przy użyciu identyfikatorów typu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
