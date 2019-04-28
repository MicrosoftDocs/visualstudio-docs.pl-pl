---
title: Idiasectioncontrib — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eada57433b37f759da51ecdb380e530f3fb77fdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839475"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
Pobiera dane opisujące wkład sekcji, czyli ciągłego bloku pamięci pochodzącego z danego obrazu compiland —.

## <a name="syntax"></a>Składnia

```
IDiaSectionContrib : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDiaSectionContrib`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Pobiera odwołanie do compiland — symbol, który zamieszczone w tej sekcji.|
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Pobiera część sekcji adres wkładu.|
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Pobiera przesunięcia część adresu wkładu.|
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Pobiera obraz wirtualny adres względny (RVA) wkładu.|
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Pobiera adres wirtualny (oceny luk w zabezpieczeniach) wkładu.|
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Pobiera liczbę bajtów w sekcji.|
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Pobiera flagę wskazującą, czy sekcja nie może być stronicowana za mało pamięci.|
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Pobiera flagę wskazującą, czy sekcja nie powinien dopełniana do następnej granicy w pamięci.|
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Pobiera flagę wskazującą, czy sekcja zawiera kod wykonywalny.|
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Pobiera flagę wskazującą, czy sekcja zawiera 16-bitowego kodu.|
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Pobiera flagę wskazującą, czy sekcja zawiera dane zainicjowane.|
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Pobiera flagę wskazującą, czy sekcja zawiera niezainicjowanych danych.|
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Pobiera flagę wskazującą, czy sekcja zawiera komentarze lub podobne informacje.|
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Pobiera flagę wskazującą, czy sekcja jest usuwany, zanim staje się częścią obrazu w pamięci.|
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Pobiera flagę wskazującą, czy sekcja jest rekord COMDAT.|
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Pobiera flagę wskazującą, czy można odrzucać sekcji.|
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Pobiera flagę wskazującą, czy nie można buforować sekcji.|
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Pobiera flagę wskazującą, czy sekcja mogą być udostępniane w pamięci.|
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Pobiera flagę wskazującą, czy sekcja jest plik wykonywalny jako kod.|
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Pobiera flagę wskazującą, czy może odczytywać sekcji.|
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Pobiera flagę wskazującą, czy mogą być zapisywane sekcji.|
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Pobiera wyboru cyklicznej kontroli nadmiarowości (CRC) danych w tej sekcji.|
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Pobiera CRC przenoszenia informacji w sekcji.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Pobiera identyfikator compiland — w sekcji.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest można uzyskać przez wywołanie [idiaenumsectioncontribs::Item —](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) i [idiaenumsectioncontribs::Next —](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) metody. Zobacz [idiaenumsectioncontribs —](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interfejsu, na przykład uzyskiwania `IDiaSectionContrib` interfejsu.

## <a name="example"></a>Przykład
Ta funkcja zawiera adres każdej sekcji oraz wszystkie skojarzone z nią symbole. Zobacz [idiaenumsectioncontribs —](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interfejsu, aby zobaczyć, jak `IDiaSectionContrib` uzyskuje się interfejs.

```C++
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)
{
    if (pSecContrib != NULL && pSession != NULL)
    {
        DWORD rva;
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )
        {
            printf( "\taddr: 0x%.8X", rva );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                        name != NULL ? name : L"",
                        szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
            }
        }
        else
        {
            DWORD isect;
            DWORD offset;
            pSecContrib->get_addressSection( &isect );
            pSecContrib->get_addressOffset( &offset );
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( SUCCEEDED( psession->findSymbolByAddr(
                                              isect,
                                              offset,
                                              SymTagNull,
                                              &pSym )
                          )
               )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                    name != NULL ? name : L"",
                    szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
            }
        }
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)
- [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
