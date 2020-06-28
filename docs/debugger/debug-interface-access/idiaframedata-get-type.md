---
title: 'IDiaFrameData:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2526fd4991677eca60b908d6ab1f4b3e6e8189af
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467198"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Pobiera typ ramki specyficznej dla kompilatora.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość z wyliczenia [stackframetypeenum —](../../debugger/debug-interface-access/stackframetypeenum.md) , która wskazuje typ ramki specyficzny dla kompilatora.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [StackFrameTypeEnum, wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md)