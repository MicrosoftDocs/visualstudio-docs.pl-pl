---
title: IDebugBoundBreakpoint2::GetBreakpointRozrozwiązany | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab88009eb1c1bbbd59bbad2dfcbf62567db3941f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735578"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Pobiera rozdzielczość punktu przerwania, który opisuje ten punkt przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Parametry
`ppBPResolution`\
[na zewnątrz] Zwraca interfejs [IDebugBreakpointResolution2,](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) który reprezentuje jedną z następujących opcji:

- Obiekt rozpoznawania punktu przerwania, który opisuje lokalizację w kodzie, w którym został powiązany punkt przerwania kodu.

- Lokalizacja danych, w której ma powiązany punkt przerwania danych.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` wartość, jeśli stan obiektu powiązanego `BPS_DELETED` punktu przerwania jest ustawiony na (część wyliczenia [BP_STATE).](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Uwagi
Wywołanie [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) metody, aby ustalić, czy rozdzielczość punktu przerwania jest dla kodu lub danych.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak `CBoundBreakpoint` zaimplementować tę metodę dla prostego obiektu, który udostępnia interfejs [IDebugBoundBreakpoint2.](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
