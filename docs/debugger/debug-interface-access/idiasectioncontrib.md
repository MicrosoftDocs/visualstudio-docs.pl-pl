---
title: IDiaSectionContrib | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 82d1a52616273a1cfe1d54580c91ec4ba6e1c09e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466071"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
Pobiera dane opisujące udział sekcji, czyli ciągły blok pamięci, który tworzy obraz przez jednostka kompilacji.

## <a name="syntax"></a>Składnia

```
IDiaSectionContrib : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaSectionContrib` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Pobiera odwołanie do symbolu jednostka kompilacji, który należy do tej sekcji.|
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Pobiera część sekcji adresu udziału.|
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Pobiera część przesunięcia adresu udziału.|
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Pobiera adres wirtualny względem obrazu (RVA) udziału.|
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Pobiera adres wirtualny (VA) udziału.|
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Pobiera liczbę bajtów w sekcji.|
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Pobiera flagę wskazującą, czy nie można stronicować sekcji poza pamięcią.|
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Pobiera flagę wskazującą, czy sekcja nie powinna być uzupełniona do następnej granicy pamięci.|
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Pobiera flagę wskazującą, czy sekcja zawiera kod wykonywalny.|
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Pobiera flagę wskazującą, czy sekcja zawiera kod 16-bitowy.|
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Pobiera flagę wskazującą, czy sekcja zawiera zainicjowane dane.|
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Pobiera flagę wskazującą, czy sekcja zawiera niezainicjowane dane.|
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Pobiera flagę wskazującą, czy sekcja zawiera komentarze lub podobne informacje.|
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Pobiera flagę wskazującą, czy sekcja zostanie usunięta przed wprowadzeniem jej do części obrazu znajdującej się w pamięci.|
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Pobiera flagę wskazującą, czy sekcja jest rekordem COMDAT.|
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Pobiera flagę wskazującą, czy sekcja może zostać odrzucona.|
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Pobiera flagę wskazującą, czy nie można buforować sekcji.|
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Pobiera flagę wskazującą, czy sekcja może być udostępniana w pamięci.|
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Pobiera flagę wskazującą, czy sekcja jest wykonywalna jako kod.|
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Pobiera flagę wskazującą, czy można odczytać sekcję.|
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Pobiera flagę wskazującą, czy można pisać sekcję.|
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Pobiera cykliczne sprawdzenie nadmiarowości (CRC) danych w sekcji.|
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Pobiera kod CRC informacji o relokacji dla sekcji.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Pobiera identyfikator jednostka kompilacji dla sekcji.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany przez wywołanie metody [IDiaEnumSectionContribs:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) i [IDiaEnumSectionContribs:: Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) . Zobacz interfejs [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) , aby zapoznać się z przykładem uzyskiwania `IDiaSectionContrib` interfejsu.

## <a name="example"></a>Przykład
Ta funkcja pokazuje adres każdej sekcji wraz ze wszystkimi skojarzonymi symbolami. Zobacz interfejs [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) , aby zobaczyć, jak `IDiaSectionContrib` uzyskiwany jest interfejs.

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
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)
- [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
