---
title: 'IDiaStackFrame:: get_lengthProlog | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthProlog method
ms.assetid: 9894c5ca-835f-41e9-a35e-70e046dfb7f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e21a5d3fce48a6919908cdaa148de7759d90189
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854921"
---
# <a name="idiastackframeget_lengthprolog"></a>IDiaStackFrame::get_lengthProlog
Pobiera liczbę bajtów kodu prologu w bloku.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lengthProlog ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów kodu prologu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)