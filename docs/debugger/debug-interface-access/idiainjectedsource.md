---
title: IDiaInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ae7095d2be479c5e7789a478b8d27632a1d2faa
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467009"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
Uzyskuje dostęp do wstrzykniętego kodu źródłowego przechowywanego w źródle danych DIA.

## <a name="syntax"></a>Składnia

```
IDiaInjectedSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaInjectedSource` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Pobiera cykliczne sprawdzenie nadmiarowości (CRC) obliczone na podstawie bajtów kodu źródłowego.|
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Pobiera liczbę bajtów kodu.|
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Pobiera nazwę pliku źródła.|
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Pobiera nazwę pliku obiektu, do którego zostało skompilowane źródło.|
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Pobiera nazwę nadaną dla kodu źródłowego niezwiązanego z plikiem; oznacza to, że kod został wstrzyknięty.|
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Pobiera wskaźnik używanej kompresji źródłowej.|
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Pobiera bajty kodu źródłowego.|

## <a name="remarks"></a>Uwagi
Wstrzykiwane źródło jest tekstem, który jest wstrzykiwany podczas kompilacji. Nie oznacza to preprocesora `#include` używanego w języku C++.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs, wywołując metodę [IDiaEnumInjectedSources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) lub [IDiaEnumInjectedSources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) . Zobacz interfejs [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , aby zapoznać się z przykładem uzyskiwania `IDiaInjectedSource` interfejsu.

## <a name="example"></a>Przykład
Ten przykład wyświetla dane dostępne w `IDiaInjectedSource` interfejsie. Alternatywne podejście przy użyciu interfejsu [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) można znaleźć w przykładowym interfejsie [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

```C++
void PrintInjectedSource(IDiaInjectedSource* pSource)
{
    ULONGLONG codeLength      = 0;
    DWORD     crc             = 0;
    DWORD     compressionType = 0;
    BSTR      sourceFilename  = NULL;
    BSTR      objectFilename  = NULL;
    BSTR      virtualFilename = NULL;

    std::cout << "Injected Source:" << std::endl;
    if (pSource != NULL)
    {
        if (pSource->get_crc(&crc) == S_OK &&
            pSource->get_sourceCompression(&compressionType) == S_OK &&
            pSource->get_length(&codeLength) == S_OK)
        {
            wprintf(L"  crc = %lu\n", crc);
            wprintf(L"  code length = %I64u\n",codeLength);
            wprintf(L"  compression type code = %lu\n", compressionType);
        }

        wprintf(L"  source filename: ");
        if (pSource->get_filename(&sourceFilename) == S_OK)
        {
            wprintf(L"%s", sourceFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  object filename: ");
        if (pSource->get_filename(&objectFilename) == S_OK)
        {
            wprintf(L"%s", objectFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  virtual filename: ");
        if (pSource->get_filename(&virtualFilename) == S_OK)
        {
            wprintf(L"%s", virtualFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        SysFreeString(sourceFilename);
        SysFreeString(objectFilename);
        SysFreeString(virtualFilename);
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)
- [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
