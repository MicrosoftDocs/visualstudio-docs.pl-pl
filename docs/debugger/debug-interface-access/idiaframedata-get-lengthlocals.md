---
title: Idiaframedata::get_lengthlocals — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6688844b5e5353d0d80ef2fb5fa2466a53f5f34a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623895"
---
# <a name="idiaframedatagetlengthlocals"></a>IDiaFrameData::get_lengthLocals
Pobiera liczbę bajtów zmienne lokalne są wypychane na stos.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca liczbę bajtów zmiennych lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość zwrócona przez tę metodę jest zwykle używanych w interpretacji ciągu program (zobacz [idiaframedata::get_program —](../../debugger/debug-interface-access/idiaframedata-get-program.md) metody dla definicji ciąg program).

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)