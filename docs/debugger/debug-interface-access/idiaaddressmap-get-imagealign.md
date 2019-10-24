---
title: 'IDiaAddressMap:: get_imageAlign | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5394580a9b0db4600a7f1e67aa8bd7f7703542
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745085"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Pobiera bieżące wyrównanie obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość wyrównania obrazu z pliku wykonywalnego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obrazy są wyrównane do określonych granic pamięci, w zależności od tego, jak obraz został załadowany i utworzony. Wyrównanie jest zwykle 1, 2, 4, 8, 16, 32 lub 64 bajtów. Wyrównanie obrazu można ustawić za pomocą wywołania metody [IDiaAddressMap::P ut_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)