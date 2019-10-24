---
title: Memorytypeenum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738633"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Określa typ pamięci do uzyskania dostępu.

## <a name="syntax"></a>Składnia

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parametry
`MemTypeCode` uzyskuje dostęp tylko do pamięci kodowej.

`MemTypeData` uzyskuje dostęp do danych lub pamięci stosu.

`MemTypeStack` uzyskuje dostęp tylko do pamięci stosu.

`MemTypeAny` uzyskuje dostęp do dowolnego rodzaju pamięci.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są przesyłane do metody [IDiaStackWalkHelper:: ReadMemory —](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) w celu ograniczenia dostępu do różnych typów pamięci.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
