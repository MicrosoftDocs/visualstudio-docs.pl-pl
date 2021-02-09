---
title: 'IDiaStackFrame:: get_systemExceptionHandling | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8211c1fc7dfc87b16f89c1f6dd181e92ec68f36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854851"
---
# <a name="idiastackframeget_systemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
Pobiera flagę wskazującą, czy obsługa wyjątku systemu jest włączona.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość `TRUE` , jeśli obsługa wyjątków systemu jest stosowana dla tej ramki; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obsługa wyjątków systemu jest również znana jako strukturalna obsługa wyjątków. Ta wartość nie jest taka sama jak obsługa wyjątków C++.

 Aby określić, czy obsługa wyjątków C++ jest skuteczna, wywołaj metodę [IDiaStackFrame:: get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)