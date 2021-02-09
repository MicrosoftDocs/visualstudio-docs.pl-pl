---
title: 'IDiaSymbol:: get_token | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_token method
ms.assetid: 7ee7a9be-a0d8-48e4-9fef-d37b3d6ae4ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d8da3cbfa085eea44af8a1caf7489aaaab83f60e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853500"
---
# <a name="idiasymbolget_token"></a>IDiaSymbol::get_token
Pobiera token metadanych zarządzanej funkcji lub zmiennej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_token ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca token metadanych zarządzanej funkcji lub zmiennej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)