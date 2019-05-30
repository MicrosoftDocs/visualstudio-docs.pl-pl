---
title: IDebugComPlusSymbolProvider::GetEntryPoint | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetEntryPoint
- GetEntryPoint
ms.assetid: 9640e121-1da1-41f9-8e66-76efca36baf2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43b99524a409d6938fd38b2623a5ec715accbbaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336793"
---
# <a name="idebugcomplussymbolprovidergetentrypoint"></a>IDebugComPlusSymbolProvider::GetEntryPoint
Pobiera punkt wejścia aplikacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEntryPoint(
    ULONG32         ulAppDomainID,
    GUID            guidModule,
    IDebugAddress** ppAddress
);
```

```csharp
int GetEntryPoint(
    uint              ulAppDomainID,
    Guid              guidModule,
    out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
[in] Identyfikator domeny aplikacji.

`guidModule`\
[in] Unikatowy identyfikator dla modułu.

`ppAddress`\
[out] Zwraca punkt wejścia, reprezentowane przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::GetEntryPoint(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugAddress **ppAddress
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppAddress, IDebugAddress *));

    METHOD_ENTRY( CDebugSymbolProvider::GetEntryPoint );

    IfFalseGo( ppAddress, E_INVALIDARG );

    *ppAddress = NULL;

    IfFailGo( GetModule( idModule, &pModule) );

    IfFailGo( pModule->GetEntryPoint( ppAddress ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetEntryPoint, hr );

    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
