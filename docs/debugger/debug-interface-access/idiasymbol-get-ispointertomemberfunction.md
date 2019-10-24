---
title: 'IDiaSymbol:: get_isPointerToMemberFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1cbbc9a38ef8d92233175380455fbe8c8291263
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740110"
---
# <a name="idiasymbolget_ispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
Określa, czy ten symbol jest wskaźnikiem do funkcji składowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isPointerToMemberFunction(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `BOOL`, który określa, czy ten symbol jest wskaźnikiem do funkcji składowej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)