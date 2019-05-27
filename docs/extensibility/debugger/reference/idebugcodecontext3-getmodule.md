---
title: IDebugCodeContext3::GetModule | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68b641f2a51e6e4286254a4d04b74a3166b671b8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206661"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Pobiera odwołanie do interfejsu debugowania modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetModule(
    IDebugModule2 **ppModule
);
```

```csharp
public int GetModule(
    out IDebugModule2 ppModule
);
```

## <a name="parameters"></a>Parametry
`ppModule`\
[out] Odwołanie do debugowania interfejsu modułu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugCodeContext** obiekt ujawniający [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) interfejsu.

```cpp
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;

    IfFalseGo( ppModule, E_INVALIDARG );
    *ppModule = NULL;

    IfFailGo( this->GetModule(&pModule) );
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
