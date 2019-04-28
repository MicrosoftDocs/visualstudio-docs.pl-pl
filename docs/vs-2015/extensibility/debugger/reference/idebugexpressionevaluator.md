---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ceffebf10838fe147475dcda54b385b844676de4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426464"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje Ewaluator wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń musi implementować ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aby uzyskać ten interfejs, Utwórz wystąpienie Ewaluator wyrażeń za pośrednictwem `CoCreateInstance` metody przy użyciu klasy ewaluatora identyfikator (CLSID). Zobacz przykład.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluator`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konwertuje ciąg wyrażenia przeanalizowany wyrażenia.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Pobiera zmienne lokalne, argumenty i inne właściwości, metody.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konwertuje metody lokalizacji i Przesunięcie adresu pamięci.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Określa język, którego należy służy do tworzenia drukowalnych wyniki.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Ustawia katalogu głównego rejestru. Używane do debugowania side-by-side.|  
  
## <a name="remarks"></a>Uwagi  
 W typowej sytuacji, aparat debugowania (DE) tworzy Ewaluator wyrażeń (EE) w wyniku wywołania [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Ponieważ DE wie, języka i dostawcy EE chce używać, DE pobiera identyfikator CLSID EE z rejestru ( [pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji `GetEEMetric`, ułatwia to pobieranie).  
  
 Po EE zostanie uruchomiony, DE wywołuje [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) można przeanalizować wyrażenia i zapisać ją w [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu. Później po wywołaniu [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) wylicza wartość wyrażenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak utworzyć ewaluatora wyrażeń, biorąc pod uwagę dostawca symboli i adres w kodzie źródłowym. W tym przykładzie użyto funkcji `GetEEMetric`, z [pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) biblioteki, dbgmetric.lib.  
  
```cpp#  
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
            CLSID clsidEE      = { 0 };  
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
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
