---
title: 'IDiaSegment:: get_read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_read method
ms.assetid: aafbc86d-352c-4e1a-911a-1472d2d59212
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faa616709015afb74db93e5a12ae8c684d93e88f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742388"
---
# <a name="idiasegmentget_read"></a>IDiaSegment::get_read
Pobiera flagę wskazującą, czy można odczytać segment.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_read ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE`, jeśli segment może być odczytany; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)