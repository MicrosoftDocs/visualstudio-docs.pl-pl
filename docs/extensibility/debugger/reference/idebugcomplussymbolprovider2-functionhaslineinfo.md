---
title: IDebugComPlusSymbolProvider2::FunctionHasLineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a6c64c77e6d8fedaf6e61f397e5dcd2a3ae577f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352722"
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
Określa, czy podana metoda ma informacje wiersza.

## <a name="syntax"></a>Składnia

```cpp
HRESULT FunctionHasLineInfo(
    IDebugAddress* pAddress
);
```

```csharp
int FunctionHasLineInfo(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[in] Adres debugowania, który jest reprezentowany przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu. Adres ten musi być METHOD_ADDRESS.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::FunctionHasLineInfo(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->FunctionHasLineInfo( address.addr.addr.addrMethod.tokMethod,
                                       address.addr.addr.addrMethod.dwVersion))
    {

        // S_FALSE indicates this method does not have line info

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
