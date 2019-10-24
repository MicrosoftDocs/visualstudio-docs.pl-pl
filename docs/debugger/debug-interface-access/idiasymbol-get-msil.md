---
title: 'IDiaSymbol:: get_msil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_msil method
ms.assetid: 43a8e003-6856-4726-aa16-c0d4dae7299b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bca44ea4b8b290089f0c1332cf5c9ba792265ee2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739790"
---
# <a name="idiasymbolget_msil"></a>IDiaSymbol::get_msil
Pobiera flagę, która określa, czy symbol odwołuje się do kodu języka pośredniego firmy Microsoft (MSIL).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_msil ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE`, jeśli symbol odwołuje się do kodu MSIL; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)