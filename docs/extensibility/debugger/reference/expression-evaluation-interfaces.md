---
title: Interfejsy oceny wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736938"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Poniżej przedstawiono interfejsy oceny [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] wyrażeń dla sdk debugowania.

## <a name="discussion"></a>Dyskusji
 Interfejsy te są używane do oceny wyrażeń w stosie wywołań w trybie przerwania. Są one implementowane tylko dla osób oceniających wyrażenie w czasie wykonywania języka wspólnego (EE).

 Każdy interfejs w tabeli pokazuje składnik, który można zaimplementować go z następującej listy:

- Aparat debugowania (DE)

- Ewaluator ekspresji (EE)

- Visual Studio (VS)

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Reprezentuje alias numeryczny dla zmiennej.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Reprezentuje alias numeryczny dla zmiennej i umożliwia ewaluatorowi wyrażeń (EE) uzyskanie domeny aplikacji dla aliasu.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Reprezentuje obiekt tablicy.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Reprezentuje obiekt tablicy zarządzanej i umożliwia oceniającemu wyrażenie (EE) określenie indeksu podstawowego (dolne granice) dla tablicy.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Reprezentuje spinacza, który wiąże symbole debugowania do rzeczywistych adresów w pamięci.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Taki sam jak interfejs [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) ale zapewnia dostęp do typów, aliasów i niestandardowych wizualizatorów.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Reprezentuje oceniającego wyrażenie.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Reprezentuje ulepszoną wersję oceniającego wyrażenie (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Reprezentuje oceniającego wyrażenie (EE) z rozszerzonym drzewem analizatora.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Reprezentuje funkcję.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Reprezentuje funkcję i zwiększa [interfejs IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umożliwia ewaluatorowi wyrażeń (EE) wyświetlanie komunikatu w oknie wyjściowym debugera.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Reprezentuje obiekt kodu zarządzanego.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfejs podstawowy reprezentujący dowolny symbol powiązany z adresem pamięci.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Taki sam jak interfejs [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) ale zapewnia dostęp do dodatkowych informacji.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Reprezentuje analizowane wyrażenie gotowe do oceny.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Reprezentuje wskaźnik.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Reprezentuje wskaźnik w drzewie analizy i rozszerza interfejs **IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Zapewnia możliwość modyfikowania wartości typu za pomocą wizualizatora typu.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Zapewnia dostęp do niestandardowych widzów i wizualizatorów typów.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Zapewnia możliwość tworzenia [obiektu IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Reprezentuje kolekcję obiektów [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)|

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Pisanie ewaluatora wyrażeń środowiska CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
