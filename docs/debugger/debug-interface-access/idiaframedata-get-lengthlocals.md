---
title: 'IDiaFrameData:: get_lengthLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c97049b1a0bdfe6b168b9141f5f36418e4a4a5b5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467331"
---
# <a name="idiaframedataget_lengthlocals"></a>IDiaFrameData::get_lengthLocals
Pobiera liczbę bajtów zmiennych lokalnych wypychanych na stosie.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów zmiennych lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość zwracana przez tę metodę jest zwykle używana w interpretacji ciągu programu (zobacz [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) Metoda dla definicji ciągu programu).

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)