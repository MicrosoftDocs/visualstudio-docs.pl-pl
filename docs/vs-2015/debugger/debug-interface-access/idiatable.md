---
title: IDiaTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682789"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wylicza tabelę źródła danych DIA.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDiaTable` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Pobiera wersję [interfejsu IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) tego modułu wyliczającego.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Pobiera nazwę tabeli.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Pobiera liczbę elementów w tabeli.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Pobiera odwołanie do określonego indeksu wpisów.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs implementuje `IEnumUnknown` metody wyliczania w przestrzeni nazw Microsoft. VisualStudio. OLE. Interop. `IEnumUnknown`Interfejs wyliczania jest znacznie bardziej wydajny w przypadku iteracji nad zawartością tabeli niż metody [IDiaTable:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) i [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .  
  
 Interpretacja `IUnknown` interfejsu zwróconego z `IDiaTable::Item` metody lub `Next` metody (w przestrzeni nazw Microsoft. VisualStudio. OLE. Interop) jest zależna od typu tabeli. Na przykład, jeśli `IDiaTable` interfejs reprezentuje listę wstrzykniętych źródeł, `IUnknown` należy zbadać interfejs dla interfejsu [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskaj ten interfejs, wywołując metodę [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) lub [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .  
  
 Następujące interfejsy są implementowane za pomocą `IDiaTable` interfejsu (oznacza to, że można wysłać zapytanie do `IDiaTable` interfejsu jednego z następujących interfejsów):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Przykład  
 Pierwsza funkcja, `ShowTableNames` , wyświetla nazwy wszystkich tabel w sesji. Druga funkcja, `GetTable` ,, przeszukuje wszystkie tabele tabeli, która implementuje określony interfejs. Trzecia funkcja, `UseTable` , pokazuje, jak używać `GetTable` funkcji.  
  
> [!NOTE]
> `CDiaBSTR` jest klasą, która zawija `BSTR` i automatycznie obsługuje zwalnianie ciągu, gdy utworzenie wystąpienia wykracza poza zakres.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2. h  
  
 Biblioteka: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
