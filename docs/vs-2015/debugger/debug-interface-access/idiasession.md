---
title: Idiasession — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2baa4b026fd9856625ce25be283c2c969f79a99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799629"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Udostępnia kontekst zapytania dla symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDiaSession`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Pobiera adres obciążenia dla pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli. Jest to tę samą wartość, która została przekazana `put_loadAddress` metody.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Ustawia adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli. **Uwaga:** ważne jest, aby wywołać tę metodę, gdy otrzymasz `IDiaSession` obiektu i przed rozpoczęciem korzystania z obiektu.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Pobiera odwołanie do zakresu globalnego.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Pobiera moduł wyliczający dla wszystkich nazwanych symboli w lokalizacjach statyczne.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Pobiera wszystkie obiekty podrzędne identyfikatora określonego elementu nadrzędnego, które jest zgodny z typem nazwy i symboli.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego adresu.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego względny adres wirtualny (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego adresu wirtualnego (oceny luk w zabezpieczeniach).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Pobiera symbol, który zawiera token określonych metadanych.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Sprawdza, czy dwa symbole są równoważne.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Pobiera symbol według unikatowego identyfikatora.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego względny adres wirtualny i przesunięcie.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego adresu wirtualnego i przesunięcie.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Pobiera compiland — i nazwa pliku źródłowego.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Pobiera pliku źródłowego przez identyfikator pliku źródłowego.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Pobiera numery wierszy w określonej źródłowe i compiland — identyfikator pliku.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Pobiera wierszy w określonej compiland —, które zawierają określony adres.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Pobiera wierszy w określonej compiland —, które zawierają określony względny adres wirtualny.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Wyszukuje informacje o numerze wiersza dla wierszy znajdujących się w zakresie określonego adresu.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Pobiera wiersze w określonym compiland — przez źródło pliku i numer wiersza.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Pobiera źródło, który został umieszczony w magazynie symboli przez dostawców atrybut lub innych części procesu kompilacji.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Pobiera sekwencję wyliczany strumieni danych debugowania.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Pobiera wyliczenie, które umożliwia klientowi wykonać iterację przez wszystkie ramki wbudowane danego adresu.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Pobiera wyliczenie, które umożliwia klientowi wykonać iterację przez wszystkie ramki wbudowane w określonym względny adres wirtualny (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Pobiera wyliczenie, które umożliwia klientowi wykonać iterację przez wszystkie ramki wbudowane na określony adres wirtualny (oceny luk w zabezpieczeniach).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w obrębie określonego zakresu adresów.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w określonym względny adres wirtualny (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w określonym wirtualnego adresu (oceny luk w zabezpieczeniach).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio w określone źródło pliku i numer wiersza.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji śródwierszowych, które odpowiadają określonej nazwie.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Zwraca wyliczenie symboli dla zmiennej, która odpowiada wartości określonego tagu w obiekcie nadrzędnym funkcji klasy zastępczej akceleratora.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Biorąc pod uwagę odpowiadająca wartość tagu, Metoda ta zwraca wyliczenie symboli, które są zawarte w funkcji klasy zastępczej akceleratora określonego elementu nadrzędnego w określonym względny adres wirtualny.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Zwraca wyliczenie symboli dla ramki wbudowane odpowiadającej nazwie funkcji określone w jednej linii.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Zwraca wyliczenie symboli dla ramek wbudowanych, które odnoszą się do określonej lokalizacji źródłowej.|  
  
## <a name="remarks"></a>Uwagi  
 Ważne jest, aby wywołać [idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metoda po utworzeniu `IDiaSession` obiektu — i wartość przekazana do `put_loadAddress` metoda musi być różna od zera — symboli jako właściwości wirtualnego adresu (oceny luk w zabezpieczeniach) dostępne. Adres obciążenia pochodzi z dowolnych program jest ładowany do debugowanego pliku wykonywalnego. Na przykład, można wywołać funkcję Win32 `GetModuleInformation` można pobrać adresu obciążenia dla pliku wykonywalnego, biorąc pod uwagę jego uchwyt do pliku wykonywalnego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać `IDiaSession` interfejsu jako część ogólne inicjowanie DIA SDK.  
  
```cpp#  
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
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [plik exe](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



