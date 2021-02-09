---
title: 'IDiaSymbol:: get_virtualBasePointerOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBasePointerOffset method
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fa72582bccd0193ab16375e04b8196275203531
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853360"
---
# <a name="idiasymbolget_virtualbasepointeroffset"></a>IDiaSymbol::get_virtualBasePointerOffset
Pobiera przesunięcie wirtualnego wskaźnika bazowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualBasePointerOffset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca przesunięcie wirtualnego wskaźnika bazowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)