---
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
ms.openlocfilehash: 85638411f7ca1da965993ffb41d98cfdbfb4198a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853773"
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