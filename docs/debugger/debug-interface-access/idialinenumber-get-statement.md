---
description: Pobiera flagę wskazującą, że informacje o tym wierszu opisują początek instrukcji zamiast wyrażenia w źródle programu.
title: 'IDiaLineNumber:: get_statement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6c36852f5aa48bcd5146419415dd06ec9d0a847
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157443"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Pobiera flagę wskazującą, że informacje o tym wierszu opisują początek instrukcji zamiast wyrażenia w źródle programu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy informacje o wierszu opisują początek instrukcji w źródle programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Instrukcje mogą obejmować wiele wierszy. Ta metoda wskazuje, czy skojarzony numer wiersza oznacza początek takiej instrukcji wielowierszowej.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
