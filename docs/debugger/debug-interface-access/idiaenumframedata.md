---
title: IDiaEnumFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e20fa21d739c79dad94a8445f6d0fe811337fd40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744562"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
Wylicza różne elementy danych ramek zawarte w źródle danych.

## <a name="syntax"></a>Składnia

```
IDiaEnumFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaEnumFrameData`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Pobiera wersję `IEnumVARIANT Interface` tego modułu wyliczającego.|
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Pobiera liczbę elementów danych ramek.|
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Pobiera element danych ramki za pomocą indeksu.|
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Pobiera określoną liczbę elementów danych ramek w sekwencji wyliczenia.|
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Pomija określoną liczbę elementów danych ramek w sekwencji wyliczenia.|
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Zwraca ramkę według względnego adresu wirtualnego (RVA).|
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Zwraca ramkę według adresu wirtualnego (VA).|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs z metody [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) . Zobacz przykład, aby uzyskać szczegółowe informacje.

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak uzyskać (funkcja `GetEnumFrameData`) i użyć (funkcji `ShowFrameData`) interfejsu `IDiaEnumFrameData`. Przykład funkcji `PrintFrameData` można znaleźć w interfejsie [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) .

```C++

      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pUnknown    = NULL;
    REFIID             iid         = __uuidof(IDiaEnumFrameData);
    IDiaEnumTables*    pEnumTables = NULL;
    IDiaTable*         pTable      = NULL;
    ULONG              celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}

void ShowFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;

    if (pEnumFrameData != NULL)
    {
        IDiaFrameData* pFrameData;
        ULONG celt = 0;

        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&
              celt == 1)
        {
            PrintFrameData(pFrameData);
            pFrameData->Release();
        }
        pEnumFrameData->Release();
    }
}
```

## <a name="requirements"></a>Wymagania
**Nagłówek:** Dia2. h

**Biblioteka:** diaguids. lib

**Dll:** msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
