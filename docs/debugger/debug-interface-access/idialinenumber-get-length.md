---
title: 'IDiaLineNumber:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f803fac1439d384133f0819859f2917072a8790
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743195"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
Pobiera liczbę bajtów w bloku.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów w bloku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Blok to długość kodu źródłowego w wierszu, reprezentowanego przez obiekt [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)