---
title: 'IDiaSymbol:: get_countLiveRanges | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03db9af960ac22c7a1ed869fbdfa4ddfebc377c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854382"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
Pobiera liczbę prawidłowych zakresów adresów skojarzonych z symbolem lokalnym.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_countLiveRanges ( 
   DWORD* count
);
```

#### <a name="parameters"></a>Parametry
 `count`

określoną Zwraca liczbę zakresów adresów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)