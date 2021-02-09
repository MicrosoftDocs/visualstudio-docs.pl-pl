---
title: 'IDiaStackFrame:: get_maxStack | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69b342520e9ae72b8d48367390d1189179e7747d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863950"
---
# <a name="idiastackframeget_maxstack"></a>IDiaStackFrame::get_maxStack
Pobiera maksymalną liczbę bajtów wypychanych na stosie w ramce.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca maksymalną liczbę bajtów wypychanych na stosie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)