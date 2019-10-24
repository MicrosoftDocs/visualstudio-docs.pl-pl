---
title: 'IDiaSymbol:: get_liveRangeStartAddressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39bf1e73d8b056c1cfcbfafd41dcbbb464c40ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739921"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Zwraca część przesunięcia adresu początkowego zakresu, w którym lokalny symbol jest prawidłowy.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parametry
 `offset`

określoną Zwraca część przesunięcia z zakresu adresów początkowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Zwrócony kod błędu oznacza, że symbol nie zawiera informacji o zakresie na żywo.

## <a name="remarks"></a>Uwagi
 Adres utworzony przez sekcję i przesunięcie to początek zakresu, w którym symbol jest prawidłowy.

 Aby uzyskać część adresu, użyj [IDiaSymbol:: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)