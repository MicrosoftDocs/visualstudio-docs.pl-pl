---
title: 'IDiaLineNumber:: get_columnNumberEnd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4433bc243a7a4f5352f0476370853572be8ddd38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743246"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Pobiera numer kolumny źródłowej opartej na jednym miejscu, w której wygaśnie wyrażenie lub instrukcję.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer kolumny, w której jest zakończona wyrażenie lub instrukcję. Jeśli wartość jest równa zero, wówczas informacje o końcu kolumny nie są obecne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość kolumny zwrócona przez tę metodę jest przesunięciem bajtów do wiersza po ostatnim znaku instrukcji w wierszu.

## <a name="see-also"></a>Zobacz także
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)