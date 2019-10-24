---
title: 'IDiaEnumFrameData:: frameByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0a6636b692a3017adb6d8b9242dca62f397bf40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744673"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Zwraca ramkę według względnego adresu wirtualnego (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametry
 relativeVirtualAddress

podczas Adres RVA ramki zainteresowania.

 ramowe

określoną Zwraca obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) reprezentujący ramkę, która zawiera podany adres.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli żadne dane ramki nie pasują do podanego adresu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)