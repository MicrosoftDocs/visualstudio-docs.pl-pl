---
title: 'IDiaStackFrame:: get_returnAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_returnAddress method
ms.assetid: 0df91981-919f-48ed-9c70-4121567d645b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fdfe3e4d52bbbfdd686c3a0394dfb5699058a69
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464976"
---
# <a name="idiastackframeget_returnaddress"></a>IDiaStackFrame::get_returnAddress
Pobiera adres zwrotny ramki.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_returnAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca adres zwrotny ramki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)