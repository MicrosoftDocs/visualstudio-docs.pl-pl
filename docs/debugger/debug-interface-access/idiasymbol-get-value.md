---
title: 'IDiaSymbol:: get_value | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_value method
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e04a21f5f0a8273975f0a0437f28808696de2da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853395"
---
# <a name="idiasymbolget_value"></a>IDiaSymbol::get_value
Pobiera wartość stałej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_value (
    VARIANT* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

[in. out] `VARIANT` Obiekt, który jest wypełniony wartością stałej.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
Dostarczony wariant musi zostać zainicjowany przed przekazaniem do tej metody. Aby uzyskać więcej informacji, zobacz przykład.

## <a name="example"></a>Przykład

```C++
void ProcessValue(IDiaSymbol *pSymbol)
{
    VARIANT value;
    value.vt = VT_EMPTY;    // Initialize variant for use.
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value.
    }
}

//----------------------------------------------------
// Alternate approach
void ProcessValue2(IDiaSymbol *pSymbol)
{
    CComVariant value;
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value
    }
}
```

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
