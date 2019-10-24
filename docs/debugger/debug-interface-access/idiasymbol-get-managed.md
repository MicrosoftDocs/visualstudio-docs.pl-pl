---
title: 'IDiaSymbol:: get_managed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_managed method
ms.assetid: a69d00be-2a89-415c-b116-385c422e2fd5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 515b8931eff37338aa53ac204c7ef61a27987aba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739813"
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

określoną Zwraca `TRUE`, jeśli symbol odwołuje się do kodu zarządzanego; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)