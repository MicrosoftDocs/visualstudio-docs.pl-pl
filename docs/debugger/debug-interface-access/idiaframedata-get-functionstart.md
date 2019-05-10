---
title: Idiaframedata::get_functionstart — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43c825bd621ada3f3e81d76f09a1f4bf9e30a67e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839982"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` Jeśli blok zawiera punkt wejścia; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieje możliwość ramka stosu nie są początku funkcji, ponieważ ramka reprezentuje wbudowane metody lub funkcji wstawione do funkcji.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)