---
description: Poniżej przedstawiono interfejsy oceny wyrażeń dla zestawu SDK debugowania programu Visual Studio.
title: Interfejsy oceny wyrażeń | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d380fcce087fad3dc6b101e78cbc514ba19b1052
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158738"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Poniżej przedstawiono interfejsy oceny wyrażeń dla [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zestawu SDK debugowania.

## <a name="discussion"></a>Dyskusja
 Te interfejsy są używane do obliczania wyrażeń w stosie wywołań w trybie przerwania. Są one implementowane tylko dla typowych ocen wyrażeń czasu wykonywania w języku (EE).

 Każdy interfejs w tabeli pokazuje składnik, który może go zaimplementować z następującej listy:

- Aparat debugowania (Niemcy)

- Ewaluatora wyrażeń (EE)

- Visual Studio (VS)

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Reprezentuje alias liczbowy dla zmiennej.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Reprezentuje alias liczbowy dla zmiennej i umożliwia ewaluatora wyrażeń (EE) uzyskanie domeny aplikacji dla aliasu.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Reprezentuje obiekt Array.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Reprezentuje zarządzany obiekt Array i pozwala ewaluatora wyrażeń (EE) określić indeks podstawowy (dolne granice) dla tablicy.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Reprezentuje spinacz, który wiąże symbole debugowania z rzeczywistymi adresami w pamięci.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Taki sam jak interfejs [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , ale zapewnia dostęp do typów, aliasów i wizualizatorów niestandardowych.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Reprezentuje ewaluatora wyrażeń.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Reprezentuje rozszerzoną wersję ewaluatora wyrażeń (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Reprezentuje ewaluatora wyrażeń (EE) z rozszerzonym drzewem analizatora składni.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Reprezentuje funkcję.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Reprezentuje funkcję i ulepsza Interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umożliwia programowi Expression ewaluatora (EE) wyświetlanie komunikatu w oknie danych wyjściowych debugera.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Reprezentuje obiekt kodu zarządzanego.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfejs podstawowy, który reprezentuje dowolny symbol powiązany z adresem pamięci.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Taki sam jak interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , ale zapewnia dostęp do dodatkowych informacji.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Przedstawia przeanalizowane wyrażenie gotowe do oceny.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Reprezentuje wskaźnik.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Reprezentuje wskaźnik w drzewie analizy i rozszerza interfejs **IDebugPointerObject** .|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Umożliwia modyfikowanie wartości typu za pomocą wizualizatora typu.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Zapewnia dostęp do niestandardowych przeglądających i wizualizatorów typów.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Zapewnia możliwość tworzenia obiektu [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Reprezentuje kolekcję obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Pisanie ewaluatora wyrażeń środowiska CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
