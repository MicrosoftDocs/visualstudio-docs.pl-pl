---
title: Przykładowa implementacja oceny wyrażeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7a19247b296d7e00a15051e75dd53536133c426
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "64858570"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykład implementacji oceny wyrażenia
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 W przypadku wyrażenia okna **czujki** program Visual Studio wywołuje [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , aby utworzyć obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` tworzy wystąpienie ewaluatora wyrażeń i [analizuje](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) je, aby uzyskać obiekt [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
 Ta implementacja programu `IDebugExpressionEvaluator::Parse` wykonuje następujące zadania:  
  
1. [Tylko C++] Analizuje wyrażenie, aby wyszukać błędy.  
  
2. Tworzy wystąpienie klasy (wywoływana `CParsedExpression` w tym przykładzie) implementującej `IDebugParsedExpression` interfejs i sklepy w klasie, które wyrażenie ma być analizowane.  
  
3. Zwraca `IDebugParsedExpression` interfejs z `CParsedExpression` obiektu.  
  
> [!NOTE]
> W przykładach, które obserwują i w próbce MyCEE, ewaluatora wyrażeń nie oddziela analizy od oceny.  
  
## <a name="managed-code"></a>Kod zarządzany  
 Jest to implementacja programu `IDebugExpressionEvaluator::Parse` w kodzie zarządzanym. Należy zauważyć, że ta wersja metody wprowadza analizę do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , ponieważ kod do analizy również szacuje się w tym samym czasie (zobacz [ocenę wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Jest to implementacja `IDebugExpressionEvaluator::Parse` w kodzie niezarządzanym. Ta metoda wywołuje funkcję pomocnika, `Parse` ,, aby przeanalizować wyrażenie i sprawdzać występowanie błędów, ale ta metoda ignoruje obliczoną wartość. Formalna ocena jest odroczona do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , gdzie wyrażenie jest analizowane podczas obliczania (patrz [Obliczenie wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
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
 [Ocenianie wyrażenia okna czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)
