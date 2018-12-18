---
title: Ocenianie wyrażenia kontrolnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89cc466ee06cd0b4834a03495088c2efdc749e5a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780298"
---
# <a name="evaluating-a-watch-expression"></a>Ocenianie wyrażenia kontrolnego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy program Visual Studio jest gotowy wyświetlić wartość wyrażenia czujki, wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) który z kolei wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Pozwala to na utworzenie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera wartość i typ wyrażenia.  
  
 W tej implementacji `IDebugParsedExpression::EvaluateSync`, wyrażenie jest analizowany i oceniane w tym samym czasie. Ta implementacja wykonuje następujące zadania:  
  
1.  Analizuje i oblicza wyrażenie w celu wygenerowania ogólnego obiekt, który przechowuje wartości i typ. W języku C#, jest reprezentowane jako `object` podczas w języku C++ jest reprezentowane jako `VARIANT`.  
  
2.  Tworzy klasę (o nazwie `CValueProperty` w tym przykładzie), który zawiera `IDebugProperty2` interfejs i są przechowywane w klasie wartość zwracaną.  
  
3.  Zwraca `IDebugProperty2` interfejs z `CValueProperty` obiektu.  
  
## <a name="managed-code"></a>Kod zarządzany  
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` w kodzie zarządzanym. Metoda pomocnika `Tokenize` analizuje wyrażenia w drzewie analizy. Funkcja Pomocnika `EvalToken` konwertuje wartość tokenu. Funkcja Pomocnika `FindTerm` rekursywnie przechodzi w drzewie analizy wywoływania `EvalToken` dla każdego węzła reprezentujący wartość i stosując wszystkie operacje (dodawania lub odejmowania) w wyrażeniu.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Niezarządzany kod  
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` w niezarządzanym kodzie. Funkcja Pomocnika `Evaluate` analizuje i oblicza wyrażenie zwraca `VARIANT` zawierający wartość wynikową. Funkcja Pomocnika `VariantValueToProperty` pakiety `VARIANT` do `CValueProperty` obiektu.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ocenianie wyrażenia okna wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Przykład implementacji oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)

