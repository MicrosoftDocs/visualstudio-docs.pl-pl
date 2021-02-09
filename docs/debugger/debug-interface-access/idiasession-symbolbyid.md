---
title: 'IDiaSession:: symbolById | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 423bf9a1c6d816d17bb36be6a4a84820617234ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864083"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Pobiera symbol przy użyciu unikatowego identyfikatora.

## <a name="syntax"></a>Składnia

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametry
`id`

podczas Unikatowy identyfikator.

`ppSymbol`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje pobrany symbol.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Określony identyfikator jest unikatową wartością używaną wewnętrznie przez DIA SDK, aby wszystkie symbole były unikatowe.

Tej metody można użyć na przykład, aby pobrać symbol reprezentujący typ innego symbolu (Zobacz przykład).

## <a name="example"></a>Przykład
Ten przykład pobiera [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący typ innego symbolu. Ten przykład pokazuje, jak używać `symbolById` metody w sesji. Prostszym podejściem jest wywołanie metody [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) w celu bezpośredniego pobrania symbolu typu.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
