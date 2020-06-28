---
title: 'IDiaLineNumber:: get_columnNumberEnd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 26645878ffca7c8c6ea0c51e02aa24668764a757
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466931"
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
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość kolumny zwrócona przez tę metodę jest przesunięciem bajtów do wiersza po ostatnim znaku instrukcji w wierszu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)