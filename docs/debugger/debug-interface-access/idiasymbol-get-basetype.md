---
title: Idiasymbol::get_basetype — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1d38e39fd7687de3ff87737b49972cb389187aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837610"
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
Pobiera typ podstawowy dla tego symbolu<em>.</em>

## <a name="syntax"></a>Składnia

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

[out] Zwraca wartość z zakresu od [basictype — wyliczenie](../../debugger/debug-interface-access/basictype.md) wyliczenie opisujące typ podstawowy elementu symbolu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
Typ podstawowy dla symbolu można określić najpierw wprowadzenie typ symbolu, a następnie odpytywanie, które zwróciło typ podstawowy typu. Należy pamiętać, że niektóre symbole nie może mieć typu podstawowego — na przykład nazwa struktury.

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
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType, wyliczenie](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
