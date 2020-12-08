---
title: Przykładowa implementacja oceny wyrażeń | Microsoft Docs
description: Dowiedz się, w jaki sposób program Visual Studio wywołuje ParseText w celu utworzenia obiektu IDebugExpression2 dla wyrażenia w systemie Windows.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ba5baf52f18f638730ecc5f3b7c016889503cbbb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847705"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykładowa implementacja oceny wyrażenia
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 W przypadku wyrażenia okna **czujki** program Visual Studio wywołuje [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , aby utworzyć obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` tworzy wystąpienie ewaluatora wyrażeń i [analizuje](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) je, aby uzyskać obiekt [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Wykonuje następujące zadania:

1. [Tylko C++] Analizuje wyrażenie, aby wyszukać błędy.

2. Tworzy wystąpienie klasy (wywoływana `CParsedExpression` w tym przykładzie), która uruchamia `IDebugParsedExpression` interfejs i przechowuje w klasie wyrażenie, które ma być analizowane.

3. Zwraca `IDebugParsedExpression` interfejs z `CParsedExpression` obiektu.

> [!NOTE]
> W przykładach, które obserwują i w próbce MyCEE, ewaluatora wyrażeń nie oddziela analizy od oceny.

## <a name="managed-code"></a>Kod zarządzany
 Poniższy kod przedstawia implementację `IDebugExpressionEvaluator::Parse` w kodzie zarządzanym. Ta wersja metody umożliwia przeanalizowanie [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , ponieważ kod do analizy również szacuje się w tym samym czasie (zobacz [ocenę wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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

## <a name="unmanaged-code"></a>Kod niezarządzany
Poniższy kod jest implementacją `IDebugExpressionEvaluator::Parse` w kodzie niezarządzanym. Ta metoda wywołuje funkcję pomocnika, `Parse` ,, aby przeanalizować wyrażenie i sprawdza pod kątem błędów, ale ta metoda ignoruje obliczoną wartość. Formalna ocena jest odroczona do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , gdzie wyrażenie jest analizowane podczas obliczania (patrz [Ocena wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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

## <a name="see-also"></a>Zobacz także
- [Oceń wyrażenie okno wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Oceń wyrażenie kontrolne](../../extensibility/debugger/evaluating-a-watch-expression.md)
