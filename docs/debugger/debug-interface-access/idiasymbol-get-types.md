---
title: Idiasymbol::get_types — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3f99530e790594e6966611b97a3d9a2c0a0cc04d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602705"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
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

[in] Rozmiar buforu do przechowywania danych.

 `pcTypes`

[out] Zwraca liczbę typów napisane, lub jeśli `types` parametr jest `NULL`, następnie całkowita liczba dostępnych typów.

 `types[]`

[out] Tablica, która ma zostać wypełniony przy użyciu [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekty reprezentujące wszystkie typy dla tego symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)