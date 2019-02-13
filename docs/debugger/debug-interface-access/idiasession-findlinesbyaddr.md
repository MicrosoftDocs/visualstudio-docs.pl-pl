---
title: Idiasession::findlinesbyaddr — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57ef75b27f90df37132ecb246b6f8d433581a696
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227462"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
Pobiera wierszy w określonej compiland —, które zawierają określony adres.

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
[in] Określa składnik sekcji określonego adresu.

`offset`  
[in] Określa przesunięcie składnik określonego adresu.

`length`  
[in] Określa liczbę bajtów zakres adresów, aby pokrywał się z tym zapytaniem.

`ppResult`  
[out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiektu, który zawiera listę wszystkich linii numery określające określony zakres adresów.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
W tym przykładzie pokazano funkcję, która uzyskuje wszystkie numery wierszy zawartych w funkcji za pomocą funkcji adres i długość.

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
[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
[IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
