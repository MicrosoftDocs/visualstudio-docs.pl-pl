---
title: 'IDiaSymbol:: get_isAcceleratorGroupSharedLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d6cf755121f851e652cce251ace2105e6773822
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740331"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Pobiera flagę wskazującą, czy symbol odnosi się do udostępnionej zmiennej lokalnej grupy w kodzie skompilowanym dla C++ akceleratora amp.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Wskaźnik do `BOOL`, który wskazuje, czy symbol odnosi się do udostępnionej zmiennej lokalnej grupy w kodzie skompilowanym dla C++ akceleratora amp. W przypadku `TRUE` metody `get_baseDataSlot` i `get_baseDataOffset` mogą być używane do uzyskiwania informacji o lokalizacji magazynu dla zmiennej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)