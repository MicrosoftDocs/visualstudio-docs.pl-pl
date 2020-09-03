---
title: 'IDiaEnumDebugStreamData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 117d16a9c010bbed2c14544f6cc94c4782701e34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468449"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Pobiera określoną liczbę rekordów w kolejności wyliczanej.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba rekordów do pobrania.

 cbData

podczas Rozmiar buforu danych w bajtach.

 pcbData

określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` ma wartość null, `pcbData` zawiera łączną liczbę bajtów danych dostępnych dla wszystkich żądanych rekordów.

 dane []

określoną Bufor, który ma zostać wypełniony danymi rekordu strumienia debugowania.

 pceltFetched

[in. out] Zwraca liczbę rekordów w `data` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej rekordów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)