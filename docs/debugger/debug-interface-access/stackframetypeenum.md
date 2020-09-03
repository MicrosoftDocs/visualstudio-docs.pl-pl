---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f83cdb163881366a1a0bede95a07e1dae1fc50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461099"
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
