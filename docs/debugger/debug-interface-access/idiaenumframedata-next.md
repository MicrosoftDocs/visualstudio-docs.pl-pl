---
description: Pobiera określoną liczbę elementów danych ramek w sekwencji wyliczenia.
title: 'IDiaEnumFrameData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adc27c29eedc98375f9feefc8872b5a75b7b219b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158037"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Pobiera określoną liczbę elementów danych ramek w sekwencji wyliczenia.

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

podczas Liczba elementów danych ramek w module wyliczającym do pobrania.

 rgelt

określoną Tablica obiektów [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) do wypełnienia z żądanymi elementami danych ramek.

 pceltFetched

określoną Zwraca liczbę elementów danych ramek w ramach pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej rekordów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
