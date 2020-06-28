---
title: 'IDiaSymbol:: get_baseSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74d775ad1035b01eed4d2537b5d388e664843a0f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464220"
---
# <a name="idiasymbolget_basesymbol"></a>IDiaSymbol::get_baseSymbol
Pobiera symbol, z którego bazuje wskaźnik.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_baseSymbol(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do symbolu, z którego bazuje wskaźnik.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)