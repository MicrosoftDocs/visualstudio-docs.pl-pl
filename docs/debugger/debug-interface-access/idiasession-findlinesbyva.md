---
title: 'IDiaSession:: findLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5e39793e2060daebf93759feb9c64622a9cf880
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465581"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Pobiera informacje o numerze wiersza dla linii zawartych w zakresie określonego adresu wirtualnego (VA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`va`

podczas Określa adres jako VA.

`length`

podczas Określa liczbę bajtów zakresu adresów, które mają być pokryte dla tego zapytania.

`ppResult`

określoną Zwraca obiekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , który zawiera listę wszystkich numerów wierszy, które obejmują określony zakres adresów.

## <a name="example"></a>Przykład
Ten przykład pokazuje funkcję, która uzyskuje wszystkie numery wierszy zawarte w funkcji przy użyciu adresu wirtualnego i długości funkcji.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
