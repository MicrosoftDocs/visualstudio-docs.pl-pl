---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729372"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Ten interfejs reprezentuje ewaluatora wyrażeń.

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Ewaluatora wyrażeń musi implementować ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Aby uzyskać ten interfejs, Utwórz wystąpienie Ewaluatora wyrażenia za pośrednictwem `CoCreateInstance` metody przy użyciu identyfikatora klasy (CLSID) ewaluatora. Zapoznaj się z przykładem.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluator` .

|Metoda|Opis|
|------------|-----------------|
|[Analizuj](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konwertuje ciąg wyrażenia na wyrażenie analizowane.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Pobiera zmienne lokalne, argumenty i inne właściwości metody.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konwertuje lokalizację metody i przesunięcie na adres pamięci.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Określa język, który ma być używany do tworzenia wyników drukowalnych.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Ustawia katalog główny rejestru. Używany do debugowania równoczesnego.|

## <a name="remarks"></a>Uwagi
W typowej sytuacji aparat debugowania (DE) tworzy wystąpienie ewaluatora wyrażeń (EE) w wyniku wywołania [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Ze względu na to, że język i dostawca wersji EE, której chce użyć, nie pobiera identyfikatora CLSID EE z rejestru ( [Pomoc zestawu SDK dla funkcji debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `GetEEMetric` ułatwia to pobieranie).

Po utworzeniu wystąpienia EE wszystkie wywołania [przeanalizują](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby przeanalizować wyrażenie i zapisać je w obiekcie [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Później wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) oblicza wyrażenie.

## <a name="requirements"></a>Wymagania
Nagłówek: EE. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak utworzyć wystąpienie ewaluatora wyrażeń z dostawcą symboli i adresem w kodzie źródłowym. Ten przykład używa funkcji, `GetEEMetric` , od [pomocników zestawu SDK dla biblioteki debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , dbgmetric. lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
