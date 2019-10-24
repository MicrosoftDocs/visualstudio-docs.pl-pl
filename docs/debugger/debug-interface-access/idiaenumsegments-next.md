---
title: 'IDiaEnumSegments:: Next | Microsoft Docs'
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
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744188"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Pobiera określoną liczbę segmentów w sekwencji wyliczenia.

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

podczas Liczba segmentów w module wyliczającym do pobrania.

 rgelt

określoną Tablica, która ma zostać wypełniona przy użyciu żądanych obiektów [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , które reprezentują segmenty.

 pceltFetched

określoną Zwraca liczbę segmentów z pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie ma więcej segmentów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)