---
description: Określa typ ramki stosu.
title: Stackframetypeenum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155307"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Określa typ ramki stosu.

## <a name="syntax"></a>Składnia

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Elementy
`FrameTypeFPO` Pominięto wskaźnik ramki; Dostępne są informacje FPO.

`FrameTypeTrap` Ramka pułapki jądra.

`FrameTypeTSS` Ramka pułapki jądra.

`FrameTypeStandard` Standardowa Ramka stosu EBP.

`FrameTypeFrameData` Pominięto wskaźnik ramki; Dostępne są informacje o danych ramek.

`FrameTypeUnknown` Ramka, która nie zawiera żadnych informacji debugowania.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
