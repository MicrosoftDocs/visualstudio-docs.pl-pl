---
title: 'IDiaSymbol:: get_liveRangeStartAddressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05355c9031aa588c8e9ed4ddceb69920fa485f51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863005"
---
# <a name="idiasymbolget_liverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Zwraca część sekcji adresu początkowego zakresu, w którym lokalny symbol jest prawidłowy.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Parametry
 `section`

określoną Zwraca część sekcji zakresu adresów początkowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Zwrócony kod błędu oznacza, że symbol nie zawiera informacji o zakresie na żywo.

## <a name="remarks"></a>Uwagi
 Adres utworzony przez sekcję i przesunięcie to początek zakresu, w którym symbol jest prawidłowy.

 Aby uzyskać część przesunięcia adresu, użyj [IDiaSymbol:: get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)