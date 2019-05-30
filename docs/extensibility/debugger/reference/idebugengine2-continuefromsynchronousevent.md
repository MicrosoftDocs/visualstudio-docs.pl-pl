---
title: IDebugEngine2::ContinueFromSynchronousEvent | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32dc338f2f2ff99d6aaff6dbd728fa3dd7fc9b84
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330150"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Wywoływane przez Menedżer debugowania sesji (SDM), aby wskazać, że w przypadku zdarzenia synchroniczne debugowania do SDM, z wcześniej wysłanych przez aparat debugowania (DE) została odbierane i przetwarzane.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

## <a name="parameters"></a>Parametry
`pEvent`\
[in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) obiekt, który reprezentuje wcześniej wysłane Zdarzenie synchroniczne, z którego narzędzie debugger teraz powinno być kontynuowane.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
DE należy sprawdzić, był źródło zdarzenia, reprezentowane przez `pEvent` parametru.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CEngine` obiekt, który implementuje [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu.

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
