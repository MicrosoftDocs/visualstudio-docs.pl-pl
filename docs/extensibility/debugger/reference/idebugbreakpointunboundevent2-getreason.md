---
title: 'IDebugBreakpointUnboundEvent2:: getpowód | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21b1eaf51f9f533fccb5275e0659367a43adb2c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900222"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
Pobiera przyczynę powiązania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason
);
```

```csharp
int GetReason(
    out enum_ BP_UNBOUND_REASON pdwUnboundReason
);
```

## <a name="parameters"></a>Parametry
`pdwUnboundReason`\
określoną Zwraca wartość z wyliczenia [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) określającą przyczynę powiązania punktu przerwania.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Przyczyna: punkt przerwania jest przełączany do innej lokalizacji po operacji Edit-and-Continue lub określenia, że punkt przerwania został powiązany z błędem.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla obiektu **CBreakpointUnboundDebugEventBase** , który uwidacznia Interfejs [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) .

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason)
{
    HRESULT hRes = E_FAIL;

    if ( EVAL(pdwUnboundReason) )
    {
        *pdwUnboundReason = m_dwReason;

        hRes = S_OK;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
