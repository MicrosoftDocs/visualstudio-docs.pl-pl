---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743333"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Pobiera bajty kodu źródłowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

podczas Liczba bajtów reprezentujących rozmiar buforu danych.

 `pcbData`

określoną Zwraca liczbę bajtów reprezentujących bajty zwrócone. Jeśli `data` jest `NULL`, `pcbData` jest łączną liczbą dostępnych bajtów danych.

 `data[]`

określoną Bufor, który ma zostać wypełniony przez bajty źródłowe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)