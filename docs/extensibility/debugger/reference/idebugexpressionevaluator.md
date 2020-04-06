---
title: IDebugExpressionAwartuator | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729372"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Ten interfejs reprezentuje oceniającego wyrażenie.

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Oceniający wyrażenie musi zaimplementować ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Aby uzyskać ten interfejs, wystąpienia oceniającego `CoCreateInstance` wyrażenie za pomocą metody przy użyciu identyfikatora klasy (CLSID) oceniającego. Zobacz przykład.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
W poniższej tabeli `IDebugExpressionEvaluator`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konwertuje ciąg wyrażenia na wyrażenie analizowane.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Pobiera zmienne lokalne, argumenty i inne właściwości metody.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konwertuje lokalizację metody i przesunięcie na adres pamięci.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Określa, który język ma być używany do tworzenia wyników drukowania.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Ustawia katalog główny rejestru. Służy do debugowania obok siebie.|

## <a name="remarks"></a>Uwagi
W typowej sytuacji aparat debugowania (DE) wystąpienia oceniającego wyrażenie (EE) w wyniku wywołania [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Ponieważ DE zna język i dostawcy EE chce użyć, DE pobiera CSID EE z rejestru [(Pomocników SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji, `GetEEMetric`, pomaga w tym pobieranie).

Po wystąpieniu EE DE wywołuje [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) do analizować wyrażenie i przechowywać go w [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu. Później wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ocenia wyrażenie.

## <a name="requirements"></a>Wymagania
Nagłówek: ee.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak utworzyć wystąpienia oceniającego wyrażenie podane dostawcy symbolu i adres w kodzie źródłowym. W tym przykładzie `GetEEMetric`użyto funkcji , z [pomocników SDK dla biblioteki debugowania,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

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
