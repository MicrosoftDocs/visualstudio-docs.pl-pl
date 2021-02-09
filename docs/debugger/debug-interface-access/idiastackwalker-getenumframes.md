---
title: 'IDiaStackWalker:: getEnumFrames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55d4a30b9f4b37274872141c6e9ac18a9aab9206
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863852"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Pobiera moduł wyliczający ramek stosu dla platform x86.

## <a name="syntax"></a>Składnia

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametry
 `pHelper`

podczas Obiekt pomocnika [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .

 `ppEnum`

określoną Zwraca obiekt [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) , który zawiera listę obiektów [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby uzyskać listę ramek stosu na dowolnej innej platformie, wywołaj metodę [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)