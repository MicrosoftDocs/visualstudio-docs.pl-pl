---
title: Idiapropertystorage — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b896cf54f06e84316f67a32c10f66dda21c2cd9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910730"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
Pozwala na trwałe właściwości zestawu właściwości DIA odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaPropertyStorage`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Pobiera wskaźnik do modułu wyliczającego dla właściwości, w tym zestawie.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Odczytuje `BOOL` wartości w zbiorze właściwości.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Odczytuje `BSTR` wartości w zbiorze właściwości.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Odczytuje `DWORD` wartości w zbiorze właściwości.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Odczytuje `LONG` wartości w zbiorze właściwości.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Odczytuje wartości właściwości w zbiorze właściwości.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Pobiera odpowiadający nazwy ciągu dla danej właściwości identyfikatorów.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Odczytuje `ULONGLONG` wartości w zbiorze właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Każdą właściwość ustawioną właściwość jest identyfikowana przez identyfikator właściwości (ID), 4 bajtowych `ULONG` wartości unikatowe dla tego zestawu. Właściwości dostępne za pośrednictwem `IDiaPropertyStorage` interfejsu odnoszą się do właściwości w interfejsie nadrzędnej. Na przykład właściwości [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) interfejs może zostać oceniony przez nazwy za pośrednictwem `IDiaPropertyStorage` interfejsu (należy jednak pamiętać, że nawet jeśli właściwość może być dostępny, nie oznacza to właściwość jest nieprawidłowa dla określonego `IDiaSymbol` obiektu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie tego interfejsu, wywołując `QueryInterface` metody na inny interfejs. Następujące interfejsy mogą być wyszukiwane dla `IDiaPropertyStorage` interfejsu:  
  
-   [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
-   [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
-   [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
-   [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
-   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
-   [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
-   [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano funkcję, która wyświetla wszystkie właściwości udostępnianych przez `IDiaPropertyStorage` obiektu. Zobacz [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu przykładowy sposób, w jaki `IDiaPropertyStorage` interfejsu są uzyskiwane z [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) interfejsu.  
  
```C++  
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)  
{  
    IEnumSTATPROPSTG* pEnumProps;  
    STATPROPSTG       prop;  
    DWORD             celt = 1;  
  
    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)  
    {  
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)  
        {  
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };  
            PROPVARIANT vt = { VT_EMPTY };  
  
            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)  
            {  
                switch( vt.vt ){  
                    case VT_BOOL:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );  
                        break;  
                    case VT_I2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );  
                        break;  
                    case VT_UI2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );  
                        break;  
                    case VT_I4:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );  
                        break;  
                    case VT_UI4:  
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );  
                        break;  
                    case VT_UI8:  
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );  
                        break;  
                    case VT_BSTR:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );  
                        break;  
                    case VT_UNKNOWN:  
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );  
                        break;  
                    case VT_SAFEARRAY:  
                        break;  
                    default:  
                       break;  
                }  
                VariantClear((VARIANTARG*) &vt);  
            }  
        }  
        pEnumProps->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession::getenumtables —](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [Idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)   
 [Idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [Idialinenumber —](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)