---
description: Pobiera wiersze w określonym jednostka kompilacji, które zawierają określony adres.
title: 'IDiaSession:: findLinesByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f90ca3fca2ff5bb41a7767c1b200518a6e2a211
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157078"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
Pobiera wiersze w określonym jednostka kompilacji, które zawierają określony adres.

## <a name="syntax"></a>Składnia

```C++
HRESULT findLinesByAddr (
    DWORD                 seg,
    DWORD                 offset,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`seg`

podczas Określa składnik sekcji określonego adresu.

`offset`

podczas Określa składnik przesunięcia określonego adresu.

`length`

podczas Określa liczbę bajtów zakresu adresów, które mają być pokryte dla tego zapytania.

`ppResult`

określoną Zwraca obiekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , który zawiera listę wszystkich numerów wierszy, które obejmują określony zakres adresów.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Ten przykład pokazuje funkcję, która uzyskuje wszystkie numery wierszy zawarte w funkcji przy użyciu adresu i długości funkcji.

```C++
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,
                                          IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                seg;
    DWORD                offset;
    ULONGLONG            length;

    if (pFunc->get_addressSection ( &seg ) == S_OK &&
        pFunc->get_addressOffset ( &offset ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
