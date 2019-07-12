---
title: Idiasymbol::get_typeids — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c7b32ab5b1965ea7a641cfac470addd2aae0ede0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64791765"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Pobiera tablicę wartości identyfikatora typu specyficznych dla kompilatora dla tego symbolu.

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

[in] Rozmiar buforu do przechowywania danych.

 `pcTypeIds`

[out] Zwraca liczbę `typeIds` zapisanych, lub jeśli `typeIds` jest `NULL`, następnie łączna liczba dostępnych identyfikatorów typu.

 `typeIds[]`

[out] Tablica, która jest wypełniona identyfikatory typów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)