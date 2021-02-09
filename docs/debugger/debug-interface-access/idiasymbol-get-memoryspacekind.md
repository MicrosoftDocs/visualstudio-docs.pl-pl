---
title: 'IDiaSymbol:: get_memorySpaceKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c763e681707d429591073ea9736a13ae5ad923d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862977"
---
# <a name="idiasymbolget_memoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
Pobiera Rodzaj przestrzeni pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_memorySpaceKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `DWORD` , który posiada Rodzaj przestrzeni pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)