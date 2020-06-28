---
title: 'IDiaStackWalkHelper:: Searchforreturnaddressstart — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68fbecf9dd085ec229f42a5af12b48d1a712ee1f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464682"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Przeszukuje określoną ramkę stosu dla adresu zwrotnego o określonym adresie stosu lub w jego prawie.

## <a name="syntax"></a>Składnia

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parametry
 `frame`

podczas Obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , który reprezentuje bieżącą ramkę stosu.

 `startAddress`

podczas Adres pamięci wirtualnej, z której należy rozpocząć wyszukiwanie.

 `ReturnAddress`

określoną Zwraca najbliższy adres zwrotny funkcji do `startAddress` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)