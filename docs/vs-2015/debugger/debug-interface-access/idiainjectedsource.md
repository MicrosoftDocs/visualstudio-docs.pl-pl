---
title: Idiainjectedsource — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 59bd1cd56ee36c5e4164549df987f789aafe32e1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760036"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uzyskuje dostęp do wprowadzony kod źródłowy, przechowywane w źródle danych DIA.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaInjectedSource`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Pobiera wyboru cyklicznej kontroli nadmiarowości (CRC) obliczonym na podstawie kodu źródłowego w bajtach.|  
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Pobiera liczbę bajtów kodu.|  
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Pobiera nazwę pliku źródłowego.|  
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Pobiera nazwę pliku obiektu, do którego został skompilowany źródła.|  
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Pobiera nazwę do kodu źródłowego-file; oznacza to, że kod, który został wprowadzony.|  
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Pobiera wskaźnik kompresji źródła używane.|  
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Pobiera bajty kodu źródłowego.|  
  
## <a name="remarks"></a>Uwagi  
 Wstrzyknięte źródło to tekst, które są wstrzykiwane podczas kompilacji. Nie oznacza to, preprocesor `#include` używany w języku C++.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie tego interfejsu, wywołując [idiaenuminjectedsources::Item —](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) lub [idiaenuminjectedsources::Next —](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) metody. Zobacz [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu, na przykład uzyskiwania `IDiaInjectedSource` interfejsu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetla określone dane, które są dostępne z `IDiaInjectedSource` interfejsu. Aby uzyskać informacje o innym podejściu przy użyciu [idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md) interfejsu, zobacz przykład w [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu.  
  
```cpp#  
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
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenuminjectedsources::Item —](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [Idiaenuminjectedsources::Next —](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
