---
title: IDiaStackFrame::get_systemExceptionHandling | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 519602b09ea1adcf00ed534ecb22b4a082018464
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838044"
---
# <a name="idiastackframegetsystemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
Pobiera flagę wskazującą, czy system obsługi wyjątków jest aktywna.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` Jeśli obsługi wyjątków systemu są włączone dla tej ramki; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obsługa wyjątków systemu jest również nazywany strukturalna Obsługa wyjątków. Nie jest tak samo jak obsługa wyjątków języka C++.

 Aby ustalić, czy C++ obsługi wyjątków jest aktywna, wywołaj [idiastackframe::get_cplusplusexceptionhandling —](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)