---
title: 'IDiaInjectedSource:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73beb6fea872da74bdce6f94e05d1c8ddc8915b7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467065"
---
# <a name="idiainjectedsourceget_length"></a>IDiaInjectedSource::get_length
Pobiera liczbę bajtów kodu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę bajtów kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość zwracana przez tę metodę jest długością kodu źródłowego i jest taka sama jak wartość zwrócona przez metodę [IDiaInjectedSource:: get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)