---
title: 'IDiaInjectedSource:: get_crc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b67072fe2928556d355aac2e65cf5d011873edd9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467128"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
Pobiera cykliczne sprawdzenie nadmiarowości (CRC) obliczone na podstawie bajtów kodu źródłowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość CRC obliczoną na podstawie bajtów kodu źródłowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)