---
title: Idiaenumframedata::Next — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55875d4ad964b958bf2fb38d259e7d4d68909cb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830108"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Pobiera określoną liczbę elementów danych ramki w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba elementów danych ramki w modułu wyliczającego do pobrania.

 rgelt

[out] Tablica [idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiektów, które ma zostać wypełniony przy użyciu elementów danych żądanego ramki.

 pceltFetched

[out] Zwraca liczbę elementów danych ramki w pobrano modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej rekordów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)