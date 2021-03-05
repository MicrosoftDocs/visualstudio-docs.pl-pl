---
description: Pobiera oryginalną wartość identyfikatora producenta sprzętu (OEM) symbolu.
title: 'IDiaSymbol:: get_oemId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a7bde81aadd179e6b09b2e46e7f0789a7433232
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155916"
---
# <a name="idiasymbolget_oemid"></a>IDiaSymbol::get_oemId
Pobiera oryginalną wartość identyfikatora producenta sprzętu (OEM) symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca unikatową wartość, która identyfikuje producenta OEM.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość ma zastosowanie tylko do symboli z typem [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) `SymTagCustomType` .

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
