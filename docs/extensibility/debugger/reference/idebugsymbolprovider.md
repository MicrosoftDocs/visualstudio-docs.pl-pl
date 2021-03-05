---
description: Ten interfejs reprezentuje dostawcę symboli, który dostarcza symbole i typy, zwracając je jako pola.
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0488520f8bde0ccd2638636810cb0055a7f3f4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168429"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Ten interfejs reprezentuje dostawcę symboli, który dostarcza symbole i typy, zwracając je jako pola.

## <a name="syntax"></a>Składnia

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Dostawca symboli musi implementować ten interfejs, aby dostarczyć informacje o symbolach i typach do ewaluatora wyrażeń.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany za pomocą `CoCreateInstance` funkcji com (dla dostawców symboli niezarządzanych) lub przez załadowanie odpowiedniego zestawu kodu zarządzanego i utworzenie wystąpienia dostawcy symboli na podstawie informacji znajdujących się w tym zestawie. Aparat debugowania tworzy wystąpienie dostawcy symboli, aby pracował w koordynacji z ewaluatora wyrażeń. Zapoznaj się z przykładem dla jednego podejścia do tworzenia wystąpienia tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDebugSymbolProvider` .

|Metoda|Opis|
|------------|-----------------|
|`Initialize`|Przestarzałe. Nie używaj.|
|`Uninitialize`|Przestarzałe. Nie używaj.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Pobiera pole, które zawiera adres debugowania.|
|`GetField`|Przestarzałe. Nie używaj.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje położenie dokumentu do tablicy adresów debugowania.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontekst dokumentu na tablicę adresów debugowania.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje adres debugowania do kontekstu dokumentu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Pobiera język używany do kompilowania kodu pod adresem debugowania.|
|`GetGlobalContainer`|Przestarzałe. Nie używaj.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Pobiera pole reprezentujące w pełni kwalifikowaną nazwę metody.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Pobiera typ pola klasy reprezentujący w pełni kwalifikowaną nazwę klasy.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Tworzy moduł wyliczający dla przestrzeni nazw skojarzonych z adresem debugowania.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje nazwę symbolu na typ symbolu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Pobiera adres debugowania, który następuje po danym adresie debugowania w metodzie.|

## <a name="remarks"></a>Uwagi
Ten interfejs mapuje pozycje dokumentu na adresy debugowania i na odwrót.

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak utworzyć wystąpienie dostawcy symboli, uwzględniając jego identyfikator GUID (aparat debugowania musi znać tę wartość).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
