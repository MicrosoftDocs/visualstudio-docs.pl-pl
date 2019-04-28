---
title: Interfejsy oceny wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a710019390120768b665cf3b27174831a67f0cc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435045"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Poniżej przedstawiono interfejsów oceny wyrażenia [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugowanie zestawu SDK.  
  
## <a name="discussion"></a>Dyskusja  
 Te interfejsy są używane do oceny wyrażenia w stosie wywołań w trybie break. Są one wykonywane tylko w przypadku ewaluatory wyrażeń czasu wykonywania w usłudze common language (EE).  
  
 Każdy interfejs w tabeli przedstawiono składnik, który można wdrożyć z następującej listy:  
  
- Debugowanie aparatu (DE)  
  
- Ewaluator wyrażeń (EE)  
  
- Visual Studio (VS)  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Reprezentuje liczbowych aliasu dla zmiennej.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Reprezentuje liczbowych alias dla zmiennej i umożliwia ewaluatora wyrażeń (EE), można uzyskać domeny aplikacji aliasu.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Reprezentuje obiekt array.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Reprezentuje obiekt tablicy zarządzanej i pozwala ewaluatora wyrażeń (EE), aby określić podstawowy indeks tablicy (dolne granice).|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Reprezentuje obiekt wiążący, że powiązań debugowania symboli do rzeczywistego adresów w pamięci.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Taki sam jak [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) ale interfejs zapewnia dostęp do typów, aliasów i wizualizatory niestandardowe.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Reprezentuje Ewaluator wyrażeń.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Reprezentuje rozbudowaną wersją ewaluatora wyrażeń (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Reprezentuje ewaluatora wyrażeń (EE) z drzewem rozszerzone analizatora.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Reprezentuje funkcję.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Reprezentuje funkcję i zwiększa [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umożliwia ewaluatora wyrażeń (EE) wyświetlić komunikat w oknie danych wyjściowych debugera.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Reprezentuje obiekt kodu zarządzanego.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Podstawowy interfejs, który reprezentuje dowolny symbol powiązany adres pamięci.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Taki sam jak [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejs, ale zapewnia dostęp do dodatkowych informacji.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Reprezentuje wyrażenie przeanalizowany, gotowy do obliczenia.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Reprezentuje wskaźnik.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Reprezentuje wskaźnik w drzewie analizy i rozszerza **IDebugPointerObject** interfejsu.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Zapewnia możliwość modyfikowania typów wartości za pośrednictwem Wizualizator typów.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Zapewnia dostęp do przeglądarek niestandardowych i wizualizatorów typu.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Zapewnia możliwość tworzenia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) obiektu.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Reprezentuje kolekcję [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
