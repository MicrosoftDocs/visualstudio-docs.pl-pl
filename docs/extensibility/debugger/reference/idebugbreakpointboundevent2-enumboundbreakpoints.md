---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f208c52bd45953aaad9efab9b6b65b15b3b759c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735359"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Tworzy wyliczacza punktów przerwania, które były powiązane w tym zdarzeniu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugBoundBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) który wylicza wszystkie punkty przerwania powiązane z tym zdarzeniem.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca . Zwraca, `S_FALSE` jeśli nie ma żadnych powiązanych punktów przerwania; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Lista powiązanych punktów przerwania jest dla osób powiązanych z tym zdarzeniem i może nie być całą listą punktów przerwania powiązanych z oczekującym punktem przerwania. Aby uzyskać listę wszystkich punktów przerwania powiązanych z oczekującym punktem przerwania, wywołaj metodę [GetPendingBreakpoint,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) aby uzyskać skojarzony obiekt [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) a następnie wywołaj metodę [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) aby uzyskać obiekt [IEnumDebugBoundBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) który zawiera wszystkie powiązane punkty przerwania dla oczekującego punktu przerwania.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak zaimplementować tę metodę dla **obiektu CBreakpointSetDebugEventBase,** który udostępnia interfejs [IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
