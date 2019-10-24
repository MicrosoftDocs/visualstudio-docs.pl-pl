---
title: 'IDiaSymbol:: get_baseSymbolId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3248721afd14ce46745e1eab40a3c4b4f9fbe76a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740933"
---
# <a name="idiasymbolget_basesymbolid"></a>IDiaSymbol::get_baseSymbolId
Pobiera identyfikator symbolu, z którego bazuje wskaźnik.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_baseSymbolId(
   DWORD *pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `DWORD`, który posiada identyfikator symbolu, z którego bazuje wskaźnik.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)