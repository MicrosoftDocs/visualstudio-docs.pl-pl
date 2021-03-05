---
description: Pobiera flagę wskazującą, czy symbol odpowiada symbolowi zakresu definicji dla składnika znacznika zmiennej wskaźnika w kodzie skompilowanym dla akceleratora C++ AMP.
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
ms.openlocfilehash: 7f46618e0dddf788f106cfccd836d3e228835735
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156245"
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
