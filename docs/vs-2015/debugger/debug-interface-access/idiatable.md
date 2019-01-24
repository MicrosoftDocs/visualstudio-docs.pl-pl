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
ms.openlocfilehash: 1b6b68ce7cd629a3c5ae1b585c91de256336f355
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760406"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wylicza DIA tabeli źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaTable`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Pobiera [interfejsu interfejs IEnumVARIANT](http://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) wersję tego modułu wyliczającego.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Pobiera nazwę tabeli.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Pobiera liczbę elementów w tabeli.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Pobiera odwołanie do indeksu dany wpis.|  
  
## <a name="remarks"></a>Uwagi  
 Implementuje ten interfejs `IEnumUnknown` metody wyliczania w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop. `IEnumUnknown` Interfejs wyliczenia jest znacznie bardziej wydajne dla Iterowanie treści niż [idiatable::get_count —](../../debugger/debug-interface-access/idiatable-get-count.md) i [idiatable::Item —](../../debugger/debug-interface-access/idiatable-item.md) metody.  
  
 Interpretacja `IUnknown` interfejsu zwróciło albo `IDiaTable::Item` metody lub `Next` metody (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) jest zależna od typu tabeli. Na przykład jeśli `IDiaTable` interfejs reprezentuje listę źródeł wprowadzonego `IUnknown` interfejsu powinny być badane dla [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie tego interfejsu, wywołując [idiaenumtables::Item —](../../debugger/debug-interface-access/idiaenumtables-item.md) lub [idiaenumtables::Next —](../../debugger/debug-interface-access/idiaenumtables-next.md) metody.  
  
 Następujące interfejsy są implementowane za pomocą `IDiaTable` interfejsu (oznacza to, że można tworzyć zapytania `IDiaTable` interfejsu dla jednego z następujących interfejsów):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Przykład  
 Pierwsza funkcja `ShowTableNames`, wyświetla nazwy wszystkich tabel w sesji. Druga funkcja `GetTable`, przeszukiwane są wszystkie tabele dla tabeli, która implementuje interfejs określony. Trzecia funkcja `UseTable`, przedstawia sposób użycia `GetTable` funkcji.  
  
> [!NOTE]
>  `CDiaBSTR` jest klasą, która otacza `BSTR` i automatycznie obsługuje zwalnianie ciągu, gdy podczas tworzenia wystąpienia wykracza poza zakres.  
  
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
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables::Item —](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
