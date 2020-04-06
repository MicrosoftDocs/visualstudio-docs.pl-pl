---
title: IDebugSymbolProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719173"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Ten interfejs reprezentuje dostawcę symboli, który udostępnia symbole i typy, zwracając je jako pola.

## <a name="syntax"></a>Składnia

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Dostawca symboli musi zaimplementować ten interfejs, aby podać informacje o symbolu i typie do oceniającego wyrażenie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany przy użyciu `CoCreateInstance` funkcji COM (dla dostawców symboli niezarządzanych) lub przez załadowanie odpowiedniego zestawu kodu zarządzanego i wystąpienie dostawcy symbolu na podstawie informacji znalezionych w tym zestawie. Aparat debugowania wystąpienia dostawcy symbolu do pracy w koordynacji z oceniającego wyrażenie. Zobacz przykład dla jednego podejścia do tworzenia wystąpienia tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
W poniższej tabeli `IDebugSymbolProvider`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|`Initialize`|Przestarzałe. Nie używaj.|
|`Uninitialize`|Przestarzałe. Nie używaj.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Pobiera pole, które zawiera adres debugowania.|
|`GetField`|Przestarzałe. Nie używaj.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje położenie dokumentu w tablicę adresów debugowania.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontekst dokumentu na tablicę adresów debugowania.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje adres debugowania w kontekście dokumentu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Pobiera język używany do kompilowania kodu pod adresem debugowania.|
|`GetGlobalContainer`|Przestarzałe. Nie używaj.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Pobiera pole reprezentujące w pełni kwalifikowaną nazwę metody.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Pobiera typ pola klasy reprezentujący w pełni kwalifikowaną nazwę klasy.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Tworzy wyliczarator dla obszarów nazw skojarzonych z adresem debugowania.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje nazwę symbolu na typ symbolu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Pobiera adres debugowania, który następuje podany adres debugowania w metodzie.|

## <a name="remarks"></a>Uwagi
Ten interfejs mapuje pozycje dokumentów na adresy debugowania i odwrotnie.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak utworzyć wystąpienia dostawcy symbolu, biorąc pod uwagę jego identyfikator GUID (aparat debugowania musi znać tę wartość).

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
