---
title: IDebugExpression2::EvaluateSync | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa9294649cae2944ad085a43ac422470995a77b3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201091"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Ta metoda oblicza wyrażenie synchronicznie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametry
`dwFlags`\
[in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie, które sterują Obliczanie wyrażenia.

`dwTimeout`\
[in] Maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

`pExprCallback`\
[in] Ten parametr jest zawsze wartość null.

`ppResult`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który zawiera wynik obliczenia wyrażenia.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Niektóre kody typowy błąd to:

|Błąd|Opis|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Inne wyrażenie jest aktualnie szacowana, a jednoczesne wyrażenia nie jest obsługiwana.|
|E_EVALUATE_TIMEOUT|Szacowanie przekroczyło limit czasu.|

## <a name="remarks"></a>Uwagi
Synchroniczne wersji ewaluacyjnej nie jest niezbędne do wysyłania zdarzeń do programu Visual Studio po zakończeniu oceny.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CExpression` obiekt, który implementuje [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
