---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2584e49209dd95c3d43673eadf72e138ac828f57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314401"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Tworzy moduł wyliczający punktów przerwania, które były powiązane dla tego zdarzenia.

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
[out] Zwraca [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) obiekt, który wylicza wszystkie punkty przerwania powiązany z tego zdarzenia.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych powiązanych punktów przerwania; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Lista powiązane punkty przerwania dla tych powiązanego z tym zdarzeniem i nie może być całą listę punktów przerwania, powiązana z oczekującym punktem przerwania. Aby uzyskać listę wszystkich punktów przerwania, powiązana z oczekującym punktem przerwania, należy wywołać [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) metodę, aby uzyskać skojarzonego [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) obiektu, a następnie wywołać [ EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) metodę, aby uzyskać [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) obiekt, który zawiera wszystkie powiązane punkty przerwania dla oczekujący punkt przerwania.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CBreakpointSetDebugEventBase** obiekt ujawniający [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfejsu.

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

## <a name="see-also"></a>Zobacz także
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
