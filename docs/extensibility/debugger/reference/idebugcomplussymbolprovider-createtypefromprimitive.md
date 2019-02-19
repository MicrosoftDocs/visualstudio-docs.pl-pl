---
title: IDebugComPlusSymbolProvider::CreateTypeFromPrimitive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
- CreateTypeFromPrimitive
ms.assetid: 37213cc2-a038-42ea-9b28-3ae40d4cfe69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9aa6a1c6c97090da451c2d9bdd08891d0f6cb0f3
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412893"
---
# <a name="idebugcomplussymbolprovidercreatetypefromprimitive"></a>IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
Tworzy typ z określonego typu pierwotnego.

## <a name="syntax"></a>Składnia

```
[C++]
HRESULT CreateTypeFromPrimitive(
    DWORD          dwPrimType,
    IDebugAddress* pAddress,
    IDebugField**  ppType
);
```

```
[C#]
int CreateTypeFromPrimitive(
    uint          dwPrimType,
    IDebugAddress pAddress,
    IDebugField   ppType
);
```

#### <a name="parameters"></a>Parametry
`dwPrimType`  
[in] Wartość z [corelementtype — wyliczenie](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) reprezentujący typu pierwotnego.

`pAddress`  
[in] Adres obiektu reprezentowanego przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

`ppType`  
[in] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt, który opisuje typ.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::CreateTypeFromPrimitive(
    DWORD dwPrimType,
    IDebugAddress* pAddress,
    IDebugField** ppType)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS addr;
    const COR_SIGNATURE* pTypeInfo = (const COR_SIGNATURE*) & dwPrimType;
    CDebugGenericParamScope* pGenScope = NULL;

    //
    // This function will only work for primitive types
    //

    METHOD_ENTRY( CDebugSymbolProvider::CreateTypeFromPrimitive );

    IfFailGo( pAddress->GetAddress( &addr ) );

    IfNullGo( pGenScope = new CDebugGenericParamScope(addr.GetModule(), addr.tokClass, addr.GetMethod()), E_OUTOFMEMORY );

    IfFailGo( CreateType( pTypeInfo,
                          1,
                          addr.GetModule(),
                          addr.GetMethod(),
                          pGenScope,
                          ppType ) );

    METHOD_EXIT( CDebugSymbolProvider::CreateTypeFromPrimitive, hr );

Error:

    RELEASE( pGenScope );
    return hr;
}
```

## <a name="see-also"></a>Zobacz też
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
