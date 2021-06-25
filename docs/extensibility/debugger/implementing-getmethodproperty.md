---
title: Implementowanie właściwości GetMethodProperty | Microsoft Docs
description: Dowiedz się, Visual Studio uzyskać informacje o bieżącej metodzie w ramce stosu przy użyciu właściwości GetDebugProperty aparatu debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab7b0ba5e51ba8ea47b473934e825b82dec320c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903297"
---
# <a name="implement-getmethodproperty"></a>Implementowanie właściwości GetMethodProperty
> [!IMPORTANT]
> W Visual Studio 2015 r. ten sposób implementowania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania ewaluatorów wyrażeń CLR, zobacz [ClR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Ewaluatory wyrażeń CLR) i Managed expression evaluator sample (Przykład ewaluatora [wyrażeń zarządzanych).](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio wywołuje metodę [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)aparatu debugowania , która z kolei wywołuje metodę [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) w celu uzyskania informacji o bieżącej metodzie w ramce stosu.

Ta implementacja `IDebugExpressionEvaluator::GetMethodProperty` programu wykonuje następujące zadania:

1. Wywołuje [getContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), przekazując [obiekt IDebugAddress.](../../extensibility/debugger/reference/idebugaddress.md) Dostawca symboli (SP) zwraca [element IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę zawierającą określony adres.

2. Uzyskuje [IDebugMethodField z](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField` .

3. Inituuje klasę (wywoływaną w tym przykładzie), która implementuje interfejs `CFieldProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) i zawiera obiekt zwrócony `IDebugMethodField` z sp.

4. Zwraca `IDebugProperty2` interfejs z `CFieldProperty` obiektu .

## <a name="managed-code"></a>Kod zarządzany
W tym przykładzie pokazano implementację `IDebugExpressionEvaluator::GetMethodProperty` w kodzie zarządzanym.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Kod niezamanageowany
W tym przykładzie pokazano `IDebugExpressionEvaluator::GetMethodProperty` implementację w kodzie niezaimażowym.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [Przykładowa implementacja lokalizacji lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)
