---
title: IDiaStackFrame::get_lengthParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthParams method
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8505556e814493078bcd3944768011a2405510c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839026"
---
# <a name="idiastackframegetlengthparams"></a>IDiaStackFrame::get_lengthParams
Pobiera liczbę bajtów parametrów wypychane na stos.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca liczbę bajtów parametrów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)