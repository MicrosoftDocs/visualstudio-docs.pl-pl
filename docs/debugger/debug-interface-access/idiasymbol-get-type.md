---
description: Pobiera symbol reprezentujący typ dla tego symbolu.
title: 'IDiaSymbol:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f0f6e86eaa78fd57d3cb62b1602111df1406f1bf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155629"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Pobiera symbol reprezentujący typ dla tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje typ tego symbolu.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
Aby określić typ symbolu, należy wywołać tę metodę i sprawdzić otrzymany obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Należy zauważyć, że istnieje możliwość, że symbol nie ma typu. Na przykład, nazwa struktury nie ma typu, ale może mieć symbole podrzędne (Użyj metody [IDiaSymbol:: findChildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md) , aby przejrzeć te elementy podrzędne).

## <a name="example"></a>Przykład

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
