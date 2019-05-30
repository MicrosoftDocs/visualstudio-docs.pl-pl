---
title: IDebugSymbolProvider | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6275cc68ac7bd9948416046f851e778ee51a83dd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347483"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Ten interfejs reprezentuje dostawcę symbol, który zawiera symbole i typy, zwracając je jako pola.

## <a name="syntax"></a>Składnia

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Dostawca symboli muszą implementować ten interfejs, można podać symboli, a następnie wpisz informacje ewaluatora wyrażeń.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskać za pomocą modelu COM `CoCreateInstance` — funkcja (dla dostawców symbol niezarządzanego) lub przez załadowanie odpowiedniego zarządzanego zestawu kodu i tworzenia wystąpienia dostawca symboli, w oparciu o informacje znajdujące się w tym zestawie. Aparat debugowania tworzy dostawca symboli do pracy w połączeniu z Ewaluator wyrażeń. Zobacz przykład jedno z podejść do tworzenia wystąpienia tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDebugSymbolProvider`.

|Metoda|Opis|
|------------|-----------------|
|`Initialize`|Przestarzałe. Nie używać.|
|`Uninitialize`|Przestarzałe. Nie używać.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Pobiera pola, które zawiera adres debugowania.|
|`GetField`|Przestarzałe. Nie używać.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje położenie dokumentu na tablicę adresów debugowania.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontekstu dokumentu na tablicę adresów debugowania.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje adres debugowania do kontekstu dokumentu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Pobiera język używany do kompilowania kodu pod adresem debugowania.|
|`GetGlobalContainer`|Przestarzałe. Nie używać.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Pobiera pole nazwy FQDN metody reprezentująca.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Pobiera typ pola klasy reprezentujące w pełni kwalifikowaną nazwę klasy.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Tworzy moduł wyliczający dla obszarów nazw skojarzonych z tym adresem debugowania.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje nazwy symbolu typ symbolu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Pobiera adres debugowania, występującego z adresu podanego debugowania w metodzie.|

## <a name="remarks"></a>Uwagi
Ten interfejs mapuje położenie dokumentu na adresy, debugowania i na odwrót.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie przedstawiono sposób tworzenia wystąpienia dostawca symboli, biorąc pod uwagę jego identyfikator GUID (aparat debugowania musi znać tej wartości).

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

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
