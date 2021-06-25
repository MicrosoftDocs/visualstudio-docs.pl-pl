---
title: Przykład implementacji oceny wyrażeń | Microsoft Docs
description: Dowiedz się, Visual Studio funkcji ParseText w celu uzyskania obiektu IDebugExpression2 dla wyrażenia okna wyrażenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902309"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykładowa implementacja oceny wyrażeń
> [!IMPORTANT]
> W Visual Studio 2015 r. ten sposób implementowania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania ewaluatorów wyrażeń CLR, zobacz [ClR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Ewaluatory wyrażeń CLR) i Managed expression evaluator Sample (Przykład zarządzanego [ewaluatora wyrażeń).](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 W przypadku **wyrażenia okna** Wyrażenie Visual Studio [obiekt ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w celu uzyskania [obiektu IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`Inicjuje ewaluator wyrażeń (EE) i wywołuje [analizę](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) w celu uzyskania [obiektu IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Program `IDebugExpressionEvaluator::Parse` wykonuje następujące zadania:

1. [Tylko C++] Analizuje wyrażenie w celu wyszukiwania błędów.

2. Iniektuje klasę (nazywaną w tym przykładzie), która uruchamia interfejs i przechowuje w klasie wyrażenie `CParsedExpression` `IDebugParsedExpression` do analizy.

3. Zwraca `IDebugParsedExpression` interfejs z `CParsedExpression` obiektu .

> [!NOTE]
> W przykładach, które są następujące, i w przykładzie MyCEE, ewaluator wyrażeń nie oddziela analizy od oceny.

## <a name="managed-code"></a>Kod zarządzany
 Poniższy kod przedstawia implementację w `IDebugExpressionEvaluator::Parse` kodzie zarządzanym. Ta wersja metody odraża analizę do [evaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ponieważ kod do analizowania również jest oceniany w tym samym czasie (zobacz [Evaluate a Watch expression](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Kod niezamanagedowany
Poniższy kod jest implementacją `IDebugExpressionEvaluator::Parse` w kodzie niezamanagedowym. Ta metoda wywołuje funkcję pomocnika , w celu analizowania wyrażenia i sprawdzania błędów, ale ta `Parse` metoda ignoruje wartość wynikową. Ocena formalna jest odroczona na [evaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gdzie wyrażenie jest analizowane podczas jego oceny (zobacz [Evaluate a Watch expression](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [Ocena wyrażenia okno wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Ocenianie wyrażenia watch](../../extensibility/debugger/evaluating-a-watch-expression.md)
