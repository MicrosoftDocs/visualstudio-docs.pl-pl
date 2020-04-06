---
title: IDebugExpression2::EvaluateAsync | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729749"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Ta metoda ocenia wyrażenie asynchronicznie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parametry
`dwFlags`\
[w] Kombinacja flag z [wyliczenia EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) które kontrolują ocenę wyrażenia.

`pExprCallback`\
[w] Ten parametr jest zawsze wartością null.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Typowy kod błędu to:

|Błąd|Opis|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Inne wyrażenie jest obecnie oceniane, a jednoczesna ocena wyrażenia nie jest obsługiwana.|

## <a name="remarks"></a>Uwagi
Ta metoda powinna zostać zwracana natychmiast po rozpoczęciu oceny wyrażenia. Po pomyślnym ocenie wyrażenia [iDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) musi zostać wysłane do wywołania zwrotnego zdarzenia [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) [dostarczonego](../../../extensibility/debugger/reference/idebugprogram2-attach.md) za pośrednictwem dołącz lub [dołącz .](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak `CExpression` zaimplementować tę metodę dla prostego obiektu, który implementuje interfejs [IDebugExpression2.](../../../extensibility/debugger/reference/idebugexpression2.md)

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
