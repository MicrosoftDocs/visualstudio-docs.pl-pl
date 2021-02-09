---
title: 'IDiaSymbol:: get_scoped | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f882a71e92056a7120eb9ea6ae3b96b6ee8ea69c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853647"
---
# <a name="idiasymbolget_scoped"></a>IDiaSymbol::get_scoped
Pobiera flagę, która określa, czy typ danych zdefiniowany przez użytkownika pojawia się w nieglobalnym zakresie leksykalnym.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_scoped ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy typ danych zdefiniowany przez użytkownika pojawia się w nieglobalnym zakresie leksykalnym; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)