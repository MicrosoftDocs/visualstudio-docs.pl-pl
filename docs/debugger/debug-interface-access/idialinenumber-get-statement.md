---
title: 'IDiaLineNumber:: get_statement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a37052944f74e36b488541074a0033f5b8aca9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743129"
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

określoną Zwraca `TRUE`, jeśli informacje o tym wierszu opisują początek instrukcji w źródle programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Instrukcje mogą obejmować wiele wierszy. Ta metoda wskazuje, czy skojarzony numer wiersza oznacza początek takiej instrukcji wielowierszowej.

## <a name="see-also"></a>Zobacz także
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)