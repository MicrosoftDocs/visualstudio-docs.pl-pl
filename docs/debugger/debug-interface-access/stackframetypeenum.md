---
title: Stackframetypeenum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738556"
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
pominięto wskaźnik `FrameTypeFPO` ramki: Dostępne są informacje FPO.

`FrameTypeTrap` ramki pułapki jądra.

`FrameTypeTSS` ramki pułapki jądra.

`FrameTypeStandard` standardowa Ramka stosu EBP.

pominięto wskaźnik `FrameTypeFrameData` ramki: Dostępne są informacje o danych ramek.

Ramka `FrameTypeUnknown`, która nie zawiera żadnych informacji debugowania.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
