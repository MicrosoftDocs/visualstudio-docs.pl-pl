---
description: 'IDiaFrameData:: get_functionStart Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.'
title: 'IDiaFrameData:: get_functionStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 996442dfbd615b7a1d4e73e2191ced36218570b4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148564"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy blok zawiera punkt wejścia; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jest możliwe, że ramka stosu nie jest początkiem funkcji, ponieważ ramka reprezentuje wbudowaną metodę lub funkcję wstawioną do funkcji.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
