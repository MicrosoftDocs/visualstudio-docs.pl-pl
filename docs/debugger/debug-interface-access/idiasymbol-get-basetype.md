---
title: 'IDiaSymbol:: get_baseType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e41b8f3825da25878ac81ba91b59106ac60d857
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863544"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
Pobiera typ podstawowy dla tego symbolu<em>.</em>

## <a name="syntax"></a>Składnia

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

określoną Zwraca wartość z wyliczenia [basictype](../../debugger/debug-interface-access/basictype.md) , określając typ podstawowy symbolu.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
Typ podstawowy dla symbolu można określić, najpierw pobierając typ symbolu, a następnie interrogating, który zwraca typ dla typu podstawowego. Należy zauważyć, że niektóre symbole nie mogą mieć typu podstawowego — na przykład nazwa struktury.

## <a name="example"></a>Przykład

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType, wyliczenie](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
