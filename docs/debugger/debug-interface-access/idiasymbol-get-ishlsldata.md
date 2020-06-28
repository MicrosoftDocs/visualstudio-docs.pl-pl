---
title: 'IDiaSymbol:: get_isHLSLData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39ea8fab6616cb64b7870cb9a1d5cd0c706fa105
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463422"
---
# <a name="idiasymbolget_ishlsldata"></a>IDiaSymbol::get_isHLSLData
Określa, czy ten symbol reprezentuje dane języka cieniowania wysokiego poziomu (HLSL).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isHLSLData(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do elementu `BOOL` , który określa, czy ten symbol reprezentuje HLSL dane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)