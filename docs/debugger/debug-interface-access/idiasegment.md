---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855b40f3d35d884a366e8fdc36ed1ec4f2bef85a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742337"
---
# <a name="idiasegment"></a>IDiaSegment
Mapuje dane z sekcji Number na segmenty przestrzeni adresowej.

## <a name="syntax"></a>Składnia

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaSegment`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Pobiera numer segmentu.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Pobiera przesunięcie w segmentach, w których rozpoczyna się sekcja.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Pobiera liczbę bajtów w segmencie.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Pobiera flagę wskazującą, czy można odczytać segment.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Pobiera flagę wskazującą, czy segment może być modyfikowany.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Pobiera flagę wskazującą, czy segment jest plikiem wykonywalnym.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Pobiera numer sekcji, który jest mapowany na ten segment.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Pobiera względny adres wirtualny (RVA) początku sekcji.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Pobiera adres wirtualny (VA) początku sekcji.|

## <a name="remarks"></a>Uwagi
Ponieważ DIA SDK już wykonuje tłumaczenia z sekcji przesunięcie do względnych adresów wirtualnych, większość aplikacji nie będzie korzystać z informacji znajdujących się na mapie segmentów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs, wywołując metodę [IDiaEnumSegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) lub [IDiaEnumSegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) . Zobacz przykład, aby uzyskać szczegółowe informacje.

## <a name="example"></a>Przykład
Ta funkcja wyświetla adres wszystkich segmentów w tabeli i najbliższy symbol.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSegments ),
                               (void**)&pSegments )
                  )
       )
    {
        CComPtr<IDiaSegment> pSegment;
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&
                celt == 1 )
        {
            DWORD rva;
            DWORD seg;

            pSegment->get_addressSection( &seg );
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )
            {
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );
                pSegment = NULL;

                CComPtr<IDiaSymbol> pSym;
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
                {
                    CDiaBSTR name;
                    DWORD    tag;

                    pSym->get_symTag( &tag );
                    pSym->get_name( &name );
                    printf( "\tClosest symbol: %ws (%ws)\n",
                            name != NULL ? name : L"",
                            szTags[ tag ] );
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
