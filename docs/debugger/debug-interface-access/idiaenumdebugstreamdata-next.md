---
title: 'IDiaEnumDebugStreamData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: acdab0a565613194c67aa85484316a235c91dbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744797"
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

określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` ma wartość NULL, `pcbData` zawiera łączną liczbę bajtów danych dostępnych dla wszystkich żądanych rekordów.

 dane []

określoną Bufor, który ma zostać wypełniony danymi rekordu strumienia debugowania.

 pceltFetched

[in. out] Zwraca liczbę rekordów w `data`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie ma więcej rekordów. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)