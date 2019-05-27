---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69afa16468865be4ae7753e46bd8e478d107b2f3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206637"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Określa, jeśli dla określonego modułu podany identyfikator domeny aplikacji, czy załadowano symbole debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
[in] Identyfikator domeny aplikacji.

`guidModule`\
[in] Unikatowy identyfikator dla modułu.

## <a name="return-value"></a>Wartość zwracana
Jeżeli symbole debugowania są ładowane, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
