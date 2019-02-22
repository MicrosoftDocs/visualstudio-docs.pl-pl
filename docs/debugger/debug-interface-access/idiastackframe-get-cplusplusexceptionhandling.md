---
title: IDiaStackFrame::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f0c2e07b5c9141b8cf31511405939fc65be6446
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615588"
---
# <a name="idiastackframegetcplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
Pobiera flagę wskazującą, czy obsługa wyjątków języka C++ jest obowiązywały.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_cplusplusExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` Jeśli obsługa wyjątków języka C++ są włączone dla tej ramki; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obsługa wyjątków języka C++ nie jest identyczna ze strukturą ani obsługi wyjątków systemu.

 Aby określić, czy mają strukturę obsługi wyjątków jest aktywna, należy wywołać [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)