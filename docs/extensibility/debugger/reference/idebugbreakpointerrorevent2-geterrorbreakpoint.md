---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe22f18d4574ffde48cea975bff8d8f5801ca465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735071"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Pobiera [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) obiektu, który opisuje powód, dla którego punkt przerwania nie został powiązany.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

## <a name="parameters"></a>Parametry
`ppErrorBP`\
[na zewnątrz] Zwraca obiekt [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) który opisuje ostrzeżenie lub błąd.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Po `IDebugErrorBreakpoint2` uzyskaniu interfejsu wywołaj [Metodę GetBreakpointResolution,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) aby uzyskać obiekt [IDebugErrorBreakpointResolution2.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) Następnie [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metoda może służyć do określenia nieprawidłowej lokalizacji, nieprawidłowe wyrażenie lub powody, dla których oczekujące punktu przerwania nie został powiązany, takich jak kod nie załadowany jeszcze i tak dalej.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak zaimplementować tę metodę dla **obiektu CBreakpointSetDebugEventBase,** który udostępnia interfejs [IDebugBreakpointErrorEvent2.](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
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
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
