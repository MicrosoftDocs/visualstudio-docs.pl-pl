---
title: Idiainjectedsource::get_source — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 604160cdaf8c1ff28b306106afe34e047768f3c4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632098"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
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

[in] Liczba bajtów, która przedstawia rozmiar buforu danych.

 `pcbData`

[out] Zwraca liczbę bajtów, która reprezentuje bajtów zwracane. Jeśli `data` jest `NULL`, następnie `pcbData` dostępnej całkowita liczba bajtów danych.

 `data[]`

[out] Buforu, który jest wypełniona bajtów źródła.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)