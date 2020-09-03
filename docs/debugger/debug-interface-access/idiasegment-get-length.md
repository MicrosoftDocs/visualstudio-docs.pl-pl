---
title: 'IDiaSegment:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_length method
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d878e831e18149df63243abd7c6a4ceee051d550
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465973"
---
# <a name="idiasegmentget_length"></a>IDiaSegment::get_length
Pobiera liczbę bajtów w segmencie.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_ length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów w segmencie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)