---
title: 'IDiaLineNumber:: get_lineNumberEnd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf1a2144831c9c0a34ebfe27cb5082887454890
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466876"
---
# <a name="idialinenumberget_linenumberend"></a>IDiaLineNumber::get_lineNumberEnd
Pobiera numer linii źródłowej, w której znajduje się instrukcja lub wyrażenie.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer wiersza, w którym znajduje się instrukcja lub wyrażenie. Jeśli wartość jest równa zero, wówczas informacje końcowe nie są obecne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)