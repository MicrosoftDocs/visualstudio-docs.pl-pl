---
description: Pobiera flagę, która określa, czy symbol odwołuje się do kodu zarządzanego.
title: 'IDiaSymbol:: get_managed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_managed method
ms.assetid: a69d00be-2a89-415c-b116-385c422e2fd5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 5e0948395876a0a52a3805e5d2059b293867a3ab
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156000"
---
# <a name="idiasymbolget_managed"></a>IDiaSymbol::get_managed
Pobiera flagę, która określa, czy symbol odwołuje się do kodu zarządzanego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_managed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy symbol odwołuje się do kodu zarządzanego; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
