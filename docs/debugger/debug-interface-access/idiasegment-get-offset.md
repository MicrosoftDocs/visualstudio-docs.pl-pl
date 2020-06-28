---
title: 'IDiaSegment:: get_offset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_offset method
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be90322d11d8676d1087ee53c914eaf7a33c518b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465966"
---
# <a name="idiasegmentget_offset"></a>IDiaSegment::get_offset
Pobiera przesunięcie (w segmentach), gdzie rozpoczyna się sekcja.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_offset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca przesunięcie (w segmentach), gdzie rozpoczyna się sekcja.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)