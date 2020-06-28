---
title: 'IDiaSymbol:: get_isAcceleratorGroupSharedLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1110f0882e8281955fa4efdf41a1355405bdd557
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463506"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Pobiera flagę wskazującą, czy symbol odnosi się do udostępnionej zmiennej lokalnej grupy w kodzie skompilowanym dla akceleratora C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Wskaźnik do elementu `BOOL` wskazuje, czy symbol odnosi się do udostępnionej zmiennej lokalnej grupy w kodzie skompilowanym dla akceleratora C++ amp. Jeśli `TRUE` `get_baseDataSlot` `get_baseDataOffset` metody i mogą być używane do uzyskiwania informacji o lokalizacji magazynu dla zmiennej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)