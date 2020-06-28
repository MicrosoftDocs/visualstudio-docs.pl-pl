---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cd255ab59c9d46676ba46baddd9cee7e3ef4cc2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461183"
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
`MemTypeCode`Uzyskuje dostęp tylko do pamięci kodowej.

`MemTypeData`Uzyskuje dostęp do danych lub pamięci stosu.

`MemTypeStack`Uzyskuje dostęp tylko do pamięci stosu.

`MemTypeAny`Uzyskuje dostęp do dowolnego rodzaju pamięci.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są przesyłane do metody [IDiaStackWalkHelper:: ReadMemory —](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) w celu ograniczenia dostępu do różnych typów pamięci.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
