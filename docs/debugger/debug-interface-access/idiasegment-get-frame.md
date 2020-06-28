---
title: 'IDiaSegment:: get_frame | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_frame method
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 962af2d8a33c385fb3a248f6564b27a9478a2e0a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465980"
---
# <a name="idiasegmentget_frame"></a>IDiaSegment::get_frame
Pobiera numer segmentu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_frame ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer segmentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)