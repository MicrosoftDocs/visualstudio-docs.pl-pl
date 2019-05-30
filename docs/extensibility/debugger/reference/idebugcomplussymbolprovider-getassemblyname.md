---
title: IDebugComPlusSymbolProvider::GetAssemblyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAssemblyName
- GetAssemblyName
ms.assetid: a08cd609-b9b9-47bd-bf73-cbf851285907
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bbb3ca2fa998cfdb362c985edb7406ca623e2f89
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336969"
---
# <a name="idebugcomplussymbolprovidergetassemblyname"></a>IDebugComPlusSymbolProvider::GetAssemblyName
Pobiera nazwę zestawu, biorąc pod uwagę jego domeny moduł i aplikacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAssemblyName(
    ULONG32 ulAppDomainID,
    GUID    guidModule,
    BSTR*   pbstrName
);
```

```csharp
int GetAssemblyName(
    uint   ulAppDomainID,
    Guid   guidModule,
    string pbstrName
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
[in] Identyfikator domeny aplikacji.

`guidModule`\
[in] Unikatowy identyfikator dla modułu.

`pbstrName`\
[out] Zwraca nazwę zestawu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::GetAssemblyName(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    Module_ID idModule(ulAppDomainID, guidModule);
    CComPtr<IMetaDataImport> pMetadata;

    METHOD_ENTRY( CDebugSymbolProvider::GetMetadataForModule );

    IfFalseGo( pbstrName, E_INVALIDARG );
    *pbstrName = NULL;

    IfFailGo( GetMetadata( idModule, &pMetadata ) );
    IfFailGo( GetAssemblyName( pMetadata, 0, pbstrName ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetMetadataForModule, hr );
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
