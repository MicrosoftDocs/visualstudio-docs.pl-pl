---
title: Idiaenumsymbolsbyaddr — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec61145d51ba383099d9b08fe0a50db10f97022
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155620"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Wylicza przy użyciu adresu różnych symboli znajdujących się w źródle danych.

## <a name="syntax"></a>Składnia

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDiaEnumSymbolsByAddr`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie w sekcji i przesunięcie.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie przez względnych adresów wirtualnych (RVA).|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie przy użyciu wirtualnego adresu (oceny luk w zabezpieczeniach).|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Pobiera następny symbole w kolejności według adresu. Aktualizuje pozycja modułu wyliczającego z kilku elementów pobrana.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Pobiera poprzednich symboli w kolejności według adresu. Aktualizuje pozycja modułu wyliczającego z kilku elementów pobrana.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Tworzy kopię obiektu.|

## <a name="remarks"></a>Uwagi
Ten interfejs zawiera symbole, pogrupowane według adresu. Do pracy z symbolami, pogrupowane według typu, na przykład `SymTagUDT` (typ zdefiniowany przez użytkownika) lub `SymTagBaseClass`, użyj [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskanie tego interfejsu, wywołując [idiasession::getsymbolsbyaddr —](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) metody.

## <a name="example"></a>Przykład
Funkcja ta wyświetla nazwę i adres wszystkie symbole, uporządkowane według względny adres wirtualny.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
[Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)  
[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
