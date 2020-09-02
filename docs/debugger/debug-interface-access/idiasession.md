---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7fb8c5336a14180b3742fa02a91e6532b6e5831
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465350"
---
# <a name="idiasession"></a>IDiaSession
Zawiera kontekst zapytania dla symboli debugowania.

## <a name="syntax"></a>Składnia

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Metody
W poniższej tabeli przedstawiono metody `IDiaSession` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Pobiera adres ładowania pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli. Jest to taka sama wartość, która została przeniesiona do `put_loadAddress` metody.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Ustawia adres ładowania pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli. **Uwaga:**  Ważne jest, aby wywołać tę metodę podczas pobierania `IDiaSession` obiektu i przed rozpoczęciem korzystania z obiektu.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Pobiera odwołanie do zakresu globalnego.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Pobiera moduł wyliczający dla wszystkich nazwanych symboli w lokalizacjach statycznych.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Pobiera wszystkie elementy podrzędne określonego identyfikatora nadrzędnego, które pasują do nazwy i typu symbolu.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Pobiera określony typ symbolu, który zawiera lub jest najbliżej podanego adresu.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Pobiera określony typ symbolu, który zawiera lub jest najbliższy do, określony względny adres wirtualny (RVA).|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Pobiera określony typ symbolu, który zawiera lub jest najbliższy do, określony adres wirtualny (VA).|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Pobiera symbol zawierający określony token metadanych.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Sprawdza, czy dwa symbole są równoważne.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Pobiera symbol przy użyciu unikatowego identyfikatora.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Pobiera określony typ symbolu, który zawiera lub jest najbliższy do, określony względny adres wirtualny i przesunięcie.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Pobiera określony typ symbolu, który zawiera lub jest najbliżej, określonego adresu wirtualnego i przesunięcia.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Pobiera plik źródłowy według jednostka kompilacji i nazwy.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Pobiera plik źródłowy według identyfikatora pliku źródłowego.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Pobiera numery wierszy w określonym jednostka kompilacji i identyfikatorze pliku źródłowego.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Pobiera wiersze w określonym jednostka kompilacji, które zawierają określony adres.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Pobiera wiersze w określonym jednostka kompilacji, które zawierają określony względny adres wirtualny.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Znajduje informacje o numerze wiersza dla linii zawartych w określonym zakresie adresów.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Pobiera wiersze w określonym jednostka kompilacji przez plik źródłowy i numer wiersza.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Pobiera źródło, które zostało umieszczone w magazynie symboli przez dostawców atrybutów lub inne składniki procesu kompilacji.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Pobiera wyliczaną sekwencję strumieni danych debugowania.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach na danym adresie.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym względnym adresie wirtualnym (RVA).|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym adresie wirtualnym (VA).|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny i są zawarte w określonym zakresie adresów.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny i są zawarte w określonym względnym adresie wirtualnym (RVA).|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny i są zawarte w określonym adresie wirtualnym (VA).|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w określonym pliku źródłowym i numerze wiersza.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza dla wszystkich funkcji, które pasują do określonej nazwy.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Zwraca Wyliczenie symboli dla zmiennej, do której odnosi się określona wartość tagu w funkcji zastępczej akceleratora nadrzędnego.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Mając odpowiednią wartość tagu, ta metoda zwraca Wyliczenie symboli, które znajdują się w określonej funkcji zastępczej akceleratora nadrzędnego w określonym względnym adresie wirtualnym.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Zwraca Wyliczenie symboli dla ramek wbudowanych odpowiadających określonej nazwie funkcji wbudowanej.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Zwraca Wyliczenie symboli dla ramek wbudowanych, które odpowiadają określonej lokalizacji źródłowej.|

## <a name="remarks"></a>Uwagi
Ważne jest, aby wywołać metodę [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) po utworzeniu `IDiaSession` obiektu — a wartość przekazaną do `put_loadAddress` metody musi być różna od zera — dla wszystkich właściwości adresów wirtualnych (VA) symboli, które mają być dostępne. Adres ładowania pochodzi z dowolnego programu załadowanego debugowanego pliku wykonywalnego. Na przykład można wywołać funkcję Win32 `GetModuleInformation` , aby pobrać adres ładowania dla pliku wykonywalnego, pod kątem dojścia do pliku wykonywalnego.

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak uzyskać `IDiaSession` interfejs w ramach ogólnej inicjalizacji DIA SDK.

```C++
CComPtr<IDiaDataSource> pSource;
ComPtr<IDiaSession> psession;

void InitializeDIA(const char *szFilename)
{
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,
                                   NULL,
                                   CLSCTX_INPROC_SERVER,
                                   __uuidof( IDiaDataSource ),
                                  (void **) &pSource);
    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename,
              szFilename,
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
