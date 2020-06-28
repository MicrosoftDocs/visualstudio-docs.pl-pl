---
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2e69a3ca233b739b32acaa769270b5253cc7232d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466988"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
Pobiera numer kolumny, w której rozpoczyna się wyrażenie lub instrukcję.

## <a name="syntax"></a>Składnia

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer kolumny, w której rozpoczyna się wyrażenie lub instrukcję. Jeśli wartość jest równa zero, wówczas informacje o kolumnie nie są obecne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość kolumny zwracana przez tę metodę jest przesunięciem bajtów do wiersza do pierwszego znaku instrukcji w wierszu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)