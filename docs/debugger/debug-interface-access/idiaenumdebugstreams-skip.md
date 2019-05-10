---
title: Idiaenumdebugstreams::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90bf6b41400143d7a6703db24c031cb3ed31de2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838187"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Pomija określoną liczbę strumieni debugowania w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 `celt`

[in] Liczba strumieni debugowania w kolejności wyliczenie, aby pominąć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie ma żadnych więcej rekordów do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)