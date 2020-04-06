---
title: Ocena wyrażenia zegarka | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738858"
---
# <a name="evaluate-a-watch-expression"></a>Ocenianie wyrażenia zegarka
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Gdy program Visual Studio jest gotowy do wyświetlania wartości wyrażenia zegarka, wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), który z kolei wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Ten proces tworzy [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera wartość i typ wyrażenia.

W tej `IDebugParsedExpression::EvaluateSync`implementacji , wyrażenie jest analizowane i oceniane w tym samym czasie. Ta implementacja wykonuje następujące zadania:

1. Analizuje i ocenia wyrażenie do produkcji obiektu ogólnego, który przechowuje wartość i jego typ. W języku C#jest to `object` reprezentowane jako while w języku C++, jest to reprezentowane jako `VARIANT`.

2. Wystąpienia klasy (o `CValueProperty` nazwie w tym przykładzie), która implementuje `IDebugProperty2` interfejs i przechowuje w klasie wartość, która ma zostać zwrócona.

3. Zwraca `IDebugProperty2` interfejs z `CValueProperty` obiektu.

## <a name="managed-code"></a>Kod zarządzany
Jest to implementacja `IDebugParsedExpression::EvaluateSync` w kodzie zarządzanym. Metoda `Tokenize` pomocnika analizuje wyrażenie w drzewie analizy. Funkcja `EvalToken` pomocnika konwertuje token na wartość. Funkcja `FindTerm` pomocnika cyklicznie przechodzi przez drzewo analizy, wywołując `EvalToken` dla każdego węzła reprezentującego wartość i stosując wszystkie operacje (dodawanie lub odejmowanie) w wyrażeniu.

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
Jest to implementacja `IDebugParsedExpression::EvaluateSync` w kodzie niezarządzanym. Funkcja `Evaluate` pomocnika analizuje i ocenia wyrażenie, zwracając `VARIANT` przytrzymanie wartości wynikowej. Funkcja `VariantValueToProperty` pomocnika łączy go `VARIANT` w `CValueProperty` obiekt.

```cpp
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
- [Ocena wyrażenia okna zegarka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Przykładowa implementacja oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
