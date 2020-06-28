---
title: 'IDiaStackFrame:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2e3001287938449313cf6fcc85d8476985993db
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464955"
---
# <a name="idiastackframeget_type"></a>IDiaStackFrame::get_type
Pobiera typ ramki.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość z wyliczenia [stackframetypeenum —](../../debugger/debug-interface-access/stackframetypeenum.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [StackFrameTypeEnum, wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md)