---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8408145d83b3b78f8392603466980495ab32d24b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467030"
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

określoną Zwraca liczbę bajtów reprezentujących bajty zwrócone. Jeśli `data` jest `NULL` , `pcbData` to całkowita liczba dostępnych bajtów danych.

 `data[]`

określoną Bufor, który ma zostać wypełniony przez bajty źródłowe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)