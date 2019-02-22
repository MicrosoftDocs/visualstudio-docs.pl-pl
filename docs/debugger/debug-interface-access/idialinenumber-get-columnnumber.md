---
title: Idialinenumber::get_columnnumber — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03d24770c90ebd225fa37dd7f60d794781e79e7e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703009"
---
# <a name="idialinenumbergetcolumnnumber"></a>IDiaLineNumber::get_columnNumber
Pobiera numer kolumny, w którym rozpoczyna się wyrażenia lub instrukcji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca numer kolumny, w którym rozpoczyna się wyrażenia lub instrukcji. Jeśli ta wartość wynosi zero, informacje o kolumnach nie jest obecny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość kolumny zwracane przez tę metodę jest bajt przesunięcie wiersza do pierwszego znaku instrukcji w tym wierszu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)