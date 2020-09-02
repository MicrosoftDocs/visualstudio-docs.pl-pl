---
title: Ocenianie wyrażenia czujki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd33a7c225e0cdc14ac3f1af9f4c78a7c1459615
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784453"
---
# <a name="evaluating-a-watch-expression"></a>Ocenianie wyrażenia kontrolnego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy program Visual Studio jest gotowy do wyświetlenia wartości wyrażenia czujka, wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , które z kolei wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Spowoduje to utworzenie obiektu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który zawiera wartość i typ wyrażenia.  
  
 W tej implementacji `IDebugParsedExpression::EvaluateSync` wyrażenie jest analizowane i oceniane w tym samym czasie. Ta implementacja wykonuje następujące zadania:  
  
1. Analizuje i szacuje wyrażenie, aby utworzyć obiekt generyczny, który przechowuje wartość i jej typ. W języku C# jest to reprezentowane przez program `object` w języku C++, który jest reprezentowany jako `VARIANT` .  
  
2. Tworzy wystąpienie klasy (wywoływana `CValueProperty` w tym przykładzie) implementującej `IDebugProperty2` interfejs i sklepy w klasie, która ma zostać zwrócona.  
  
3. Zwraca `IDebugProperty2` interfejs z `CValueProperty` obiektu.  
  
## <a name="managed-code"></a>Kod zarządzany  
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` w kodzie zarządzanym. Metoda pomocnika `Tokenize` analizuje wyrażenie w drzewie analizy. Funkcja pomocnika `EvalToken` konwertuje token na wartość. Funkcja pomocnika `FindTerm` cyklicznie przechodzi drzewo analizy, wywołując `EvalToken` dla każdego węzła reprezentującego wartość i stosując wszystkie operacje (Dodawanie lub odejmowanie) w wyrażeniu.  
  
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
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` kodu niezarządzanego. Funkcja pomocnika `Evaluate` analizuje i szacuje wyrażenie, zwracając element `VARIANT` utrzymujący wartość wynikową. Funkcja pomocnika `VariantValueToProperty` `VARIANT` tworzy pakiet do `CValueProperty` obiektu.  
  
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
 [Ocenianie wyrażenia okna czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Przykład implementacji oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
