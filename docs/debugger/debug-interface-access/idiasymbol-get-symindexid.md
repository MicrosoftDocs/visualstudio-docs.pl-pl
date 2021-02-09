---
title: 'IDiaSymbol:: get_symIndexId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symIndexId method
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 810de26d9bef93308744a161f6638fb61913dea2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853563"
---
# <a name="idiasymbolget_symindexid"></a>IDiaSymbol::get_symIndexId
Pobiera unikatowy identyfikator symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_symIndexId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca identyfikator symbolu symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Identyfikator jest unikatową wartością utworzoną przez DIA SDK, aby oznaczyć wszystkie symbole jako unikatowe.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)