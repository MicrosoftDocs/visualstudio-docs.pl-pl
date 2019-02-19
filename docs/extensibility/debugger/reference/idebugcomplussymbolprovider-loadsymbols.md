---
title: IDebugComPlusSymbolProvider::LoadSymbols | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- LoadSymbols
- IDebugComPlusSymbolProvider::LoadSymbols
ms.assetid: 3499680d-0b9a-4f20-8432-c89a41b29b87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1469c2a0d8332371bb38be2616ae7dcf6a61fe37
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413374"
---
# <a name="idebugcomplussymbolproviderloadsymbols"></a>IDebugComPlusSymbolProvider::LoadSymbols
Ładuje symbole debugowania określony w pamięci.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LoadSymbols(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath
);
```

```csharp
int LoadSymbols(
    uint   ulAppDomainID,
    Guid   guidModule,
    ulong  baseAddress,
    object pUnkMetadataImport,
    string bstrModuleName,
    string bstrSymSearchPath
);
```

#### <a name="parameters"></a>Parametry
`ulAppDomainID`  
[in] Identyfikator domeny aplikacji.

`guidModule`  
[in] Unikatowy identyfikator mondule.

`baseAddress`  
[in] Adres podstawowy pamięci.

`pUnkMetadataImport`  
[in] Obiekt, który zawiera metadane symbolu.

`bstrModuleName`  
[in] Nazwa modułu.

`bstrSymSearchPath`  
[in] Ścieżka do wyszukiwania pliku symboli.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* _pMetadata,
    BSTR bstrModule,
    BSTR bstrSearchPath)
{
    return LoadSymbolsWithCorModule(ulAppDomainID, guidModule, baseOffset, _pMetadata, NULL, bstrModule, bstrSearchPath);
}
```

## <a name="see-also"></a>Zobacz też
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
