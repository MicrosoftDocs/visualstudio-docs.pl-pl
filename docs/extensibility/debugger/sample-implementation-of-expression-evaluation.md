---
title: Przykładowa realizacja oceny wyrażenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713099"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykładowa implementacja oceny wyrażenia
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [próbka ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 W przypadku wyrażenia okna **czujki** program Visual Studio wywołuje [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) do produkcji obiektu [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`wystąpienia oceniającego wyrażenie (EE) i wywołuje [Parse,](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) aby uzyskać [obiekt IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Wykonuje `IDebugExpressionEvaluator::Parse` następujące zadania:

1. [Tylko C++] Analizuje wyrażenie, aby wyszukać błędy.

2. Wystąpienia klasy (o `CParsedExpression` nazwie w tym przykładzie), który uruchamia `IDebugParsedExpression` interfejs i przechowuje w klasie wyrażenie, które mają być analizowane.

3. Zwraca `IDebugParsedExpression` interfejs z `CParsedExpression` obiektu.

> [!NOTE]
> W przykładach, które następują i w przykładzie MyCEE oceniający wyrażenie nie oddziela analizowania od oceny.

## <a name="managed-code"></a>Kod zarządzany
 Poniższy kod przedstawia `IDebugExpressionEvaluator::Parse` implementację w kodzie zarządzanym. Ta wersja metody odracza analizowanie do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jako kod do analizowania również ocenia w tym samym czasie (zobacz [Oceń wyrażenie Czujka).](../../extensibility/debugger/evaluating-a-watch-expression.md)

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

## <a name="unmanaged-code"></a>Niezarządzany kod
Poniższy kod jest `IDebugExpressionEvaluator::Parse` implementacją w kodzie niezarządzanym. Ta metoda wywołuje funkcję `Parse`pomocnika, , aby przeanalizować wyrażenie i sprawdzić, czy nie ma błędów, ale ta metoda ignoruje wynikową wartość. Ocena formalna jest odroczona do [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gdzie wyrażenie jest analizowane podczas jego oceny (zobacz [Oceń wyrażenie Czujka).](../../extensibility/debugger/evaluating-a-watch-expression.md)

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
- [Ocena wyrażenia okna czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Ocena wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)
