---
title: Idiaenumframedata::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d747149e18f831b9f57249503a64c37141c4daa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833601"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Pomija określoną liczbę elementów danych ramki w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba elementów danych ramki w kolejności wyliczenie, aby pominąć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie ma żadnych więcej rekordów do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)