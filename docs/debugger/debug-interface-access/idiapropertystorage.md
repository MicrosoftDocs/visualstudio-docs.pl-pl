---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba4cdb5f74cedf13cfb74b5aff6d43d24534eab9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466484"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
Umożliwia odczytywanie trwałych właściwości zestawu właściwości DIA.

## <a name="syntax"></a>Składnia

```
IDiaPropertyStorage : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaPropertyStorage` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Pobiera wskaźnik do modułu wyliczającego dla właściwości w tym zestawie.|
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Odczytuje `BOOL` wartości w zestawie właściwości.|
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Odczytuje `BSTR` wartości w zestawie właściwości.|
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Odczytuje `DWORD` wartości w zestawie właściwości.|
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Odczytuje `LONG` wartości w zestawie właściwości.|
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Odczytuje wartości właściwości w zestawie właściwości.|
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Pobiera odpowiednie nazwy ciągów dla danego identyfikatorów właściwości.|
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Odczytuje `ULONGLONG` wartości w zestawie właściwości.|

## <a name="remarks"></a>Uwagi
Każda właściwość w ramach zestawu właściwości jest identyfikowana przez identyfikator właściwości (identyfikator), a wartość 4-bajtowa `ULONG` unikatowa dla tego zestawu. Właściwości uwidocznione za pomocą `IDiaPropertyStorage` interfejsu odpowiadają właściwościom dostępnym w interfejsie nadrzędnym. Na przykład właściwości interfejsu [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) są dostępne przez nazwę za pośrednictwem `IDiaPropertyStorage` interfejsu (należy zauważyć, że mimo że właściwość może być dostępna, nie oznacza to, że właściwość jest prawidłowa dla określonego `IDiaSymbol` obiektu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs, wywołując `QueryInterface` metodę w innym interfejsie. Dla interfejsu można zbadać następujące interfejsy `IDiaPropertyStorage` :

- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

## <a name="example"></a>Przykład
Ten przykład pokazuje funkcję, która wyświetla wszystkie właściwości uwidocznione przez `IDiaPropertyStorage` obiekt. Zobacz interfejs [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , aby zapoznać się z przykładem sposobu `IDiaPropertyStorage` uzyskiwania interfejsu z interfejsu [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

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
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
