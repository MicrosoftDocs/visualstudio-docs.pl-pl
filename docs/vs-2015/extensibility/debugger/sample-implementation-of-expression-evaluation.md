---
title: Przykładowy implementacji oceny wyrażenia | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436695"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykład implementacji oceny wyrażenia
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Dla **Obejrzyj** wyrażenia okna wyrażeń, wywołania programu Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) do produkcji [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu. `IDebugExpressionContext2::ParseText` tworzy wystąpienie ewaluatora wyrażeń (EE) i wywołuje [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) uzyskać [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.  
  
 Ta implementacja `IDebugExpressionEvaluator::Parse` wykonuje następujące zadania:  
  
1. [C++ tylko] Analizuje wyrażenia, aby wyszukać błędy.  
  
2. Tworzy klasę (o nazwie `CParsedExpression` w tym przykładzie), który zawiera `IDebugParsedExpression` interfejs i są przechowywane w klasie wyrażenie które ma zostać przeanalizowany.  
  
3. Zwraca `IDebugParsedExpression` interfejs z `CParsedExpression` obiektu.  
  
> [!NOTE]
> W przykładach i w przykładzie MyCEE Ewaluator wyrażeń nie należy oddzielić analizy z oceny.  
  
## <a name="managed-code"></a>Kod zarządzany  
 Jest to implementacja `IDebugExpressionEvaluator::Parse` w kodzie zarządzanym. Należy pamiętać, że ta wersja metody odracza analizy do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jako kod do analizowania oblicza również w tym samym czasie (zobacz [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Jest to implementacja `IDebugExpressionEvaluator::Parse` w niezarządzanym kodzie. Ta metoda wywołuje funkcję Pomocnika `Parse`, można przeanalizować wyrażenia i sprawdź błędy, ale ta metoda ignoruje wartość wynikową. Posiadanie oceny jest odroczone do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gdy wyrażenie jest analizowany, gdy zostanie ono ocenione (zobacz [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 [Ocenianie wyrażenia okna wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)
