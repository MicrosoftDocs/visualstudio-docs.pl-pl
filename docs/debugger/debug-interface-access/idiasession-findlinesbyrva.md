---
title: Idiasession::findlinesbyrva — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4316bfa423392a98946fc0bb86af2f2e9836aba2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827690"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Pobiera wierszy w określonej compiland —, które zawierają określony względny adres wirtualny (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findLinesByRVA ( 
    DWORD                 rva,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`rva`

[in] Określa adres jako adres RVA.

`length`

[in] Określa liczbę bajtów zakres adresów, aby pokrywał się z tym zapytaniem.

`ppResult`

[out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiektu, który zawiera listę wszystkich linii numery określające określony zakres adresów.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
W tym przykładzie pokazano funkcję, która uzyskuje wszystkie numery wierszy zawartych w określonej funkcji przy użyciu funkcji względny adres wirtualny i długości.

```C++
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                rva;
    ULONGLONG            length;

    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
