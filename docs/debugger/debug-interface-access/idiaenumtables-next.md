---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743739"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Pobiera określoną liczbę tabel w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 `celt`

podczas Liczba tabel w module wyliczającym do pobrania.

 `rgelt`

określoną Tablica, która ma zostać wypełniona obiektami [IDiaTable](../../debugger/debug-interface-access/idiatable.md) , które reprezentują żądane tabele.

 `pceltFetched`

określoną Zwraca liczbę tabel w ramach pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie ma więcej tabel. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)