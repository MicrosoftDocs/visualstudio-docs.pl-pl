---
description: Określa typ pamięci do uzyskania dostępu.
title: Memorytypeenum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 557991a66f7e70dedcd7dad2a05d7e25fd0cd6b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155370"
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
`MemTypeCode` Uzyskuje dostęp tylko do pamięci kodowej.

`MemTypeData` Uzyskuje dostęp do danych lub pamięci stosu.

`MemTypeStack` Uzyskuje dostęp tylko do pamięci stosu.

`MemTypeAny` Uzyskuje dostęp do dowolnego rodzaju pamięci.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są przesyłane do metody [IDiaStackWalkHelper:: ReadMemory —](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) w celu ograniczenia dostępu do różnych typów pamięci.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
