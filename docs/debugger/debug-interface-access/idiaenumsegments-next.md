---
title: Idiaenumsegments::Next — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9b0f0d06ae5303277c296fd56e36e60b9a6f022
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829644"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Pobiera określoną liczbę segmentów w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba segmentów w modułu wyliczającego do pobrania.

 rgelt

[out] Tablica, która ma być wypełnione z żądaną [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) obiekty reprezentujące segmenty.

 pceltFetched

[out] Zwraca liczbę segmentów w pobrano modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej segmentów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)