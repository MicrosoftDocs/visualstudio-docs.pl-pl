---
title: 'IDiaSymbol:: get_isAcceleratorPointerTagLiveRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a0e2d22da73402c7eb68e2a84cfe98e59fc0832
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863257"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Pobiera flagę wskazującą, czy symbol odpowiada *symbolowi zakresu definicji* dla składnika znacznika zmiennej wskaźnika w kodzie skompilowanym dla akceleratora C++ amp. Symbol zakresu definicji jest lokalizacją zmiennej dla zakresu adresów.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Wskaźnik do elementu `BOOL` wskazuje, czy symbol odpowiada symbolowi zakresu definicji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)