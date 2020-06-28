---
title: 'IDiaStackFrame:: get_base | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_base method
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26717fc229bcd167bb344db6a82d81902de1d890
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465116"
---
# <a name="idiastackframeget_base"></a>IDiaStackFrame::get_base
Pobiera adres podstawowy ramki.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_base ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca adres podstawowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)