---
title: 'IDiaEnumDebugStreams:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get_Count method
ms.assetid: 5c13fa9a-b35e-47b0-806f-1f53bfe1ba89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf04ddf455bbd9d3c006e8c17149412d5ed77cce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468414"
---
# <a name="idiaenumdebugstreamsget_count"></a>IDiaEnumDebugStreams::get_Count
Pobiera liczbę strumieni debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_Count( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę strumieni debugowania dostępnych w tym module wyliczającym.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)