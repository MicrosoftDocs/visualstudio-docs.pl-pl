---
title: IDiaSymbol::get_stride | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c581668668a208a9bcf35a1b39d1b3d384a4f8a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62841617"
---
# <a name="idiasymbolgetstride"></a>IDiaSymbol::get_stride
Pobiera stride macierzy lub strided tablicy.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_stride(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Wskaźnik do `DWORD` przechowuje krok.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)