---
title: 'IDiaSymbol:: get_targetOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetOffset method
ms.assetid: 7d141223-132a-409c-a5a4-94f97340313c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f16521314971617f07c4adabafa14187c3c7b7c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853542"
---
# <a name="idiasymbolget_targetoffset"></a>IDiaSymbol::get_targetOffset
Pobiera sekcję przesunięcia elementu docelowego thunk.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_targetOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca część przesunięcia adresu docelowego thunk.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)