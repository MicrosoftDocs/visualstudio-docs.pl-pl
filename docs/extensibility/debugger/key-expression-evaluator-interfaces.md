---
title: Interfejsy oceniającego kluczowe wyrażenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738491"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfejsy oceniającego kluczowe wyrażenia
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Podczas pisania oceniającego wyrażenie (EE), wraz z kontekstu oceny, należy zapoznać się z następujących interfejsów.

## <a name="interface-descriptions"></a>Opisy interfejsu

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Ma jedną metodę [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), która pobiera strukturę danych, która reprezentuje bieżący punkt wykonania. Ta struktura danych jest jednym z trzech argumentów, które aparat debugowania (DE) przekazuje do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metody do oceny wyrażenia. Ten interfejs jest zazwyczaj implementowane przez dostawcę symbolu.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Ma [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) metody, która pobiera obszar pamięci, który zawiera bieżącą wartość symbolu. Biorąc pod uwagę zarówno metody zawierającej, reprezentowane przez [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu, a sam symbol, `IDebugBinder::Bind` reprezentowane przez [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu, zwraca wartość symbolu. `IDebugBinder`jest zazwyczaj wdrażany przez DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Reprezentuje prosty typ danych. W przypadku bardziej złożonych typów, takich jak tablice i metody, należy użyć pochodnych interfejsów [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) i [IDebugMethodField,](../../extensibility/debugger/reference/idebugmethodfield.md) odpowiednio. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) to kolejny ważny interfejs pochodny, który reprezentuje symbole zawierające inne symbole, takie jak metody lub klasy. Interfejs `IDebugField` (i jego pochodne) jest zazwyczaj implementowane przez dostawcę symbolu.

     Obiekt `IDebugField` może służyć do znajdowania nazwy i typu symbolu i, wraz z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) obiektu, może służyć do znalezienia jego wartości.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Reprezentuje rzeczywiste bity wartości w czasie wykonywania symbolu. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) przyjmuje obiekt [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) który reprezentuje symbol, i zwraca obiekt [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) Metoda zwraca wartość symbolu w buforze pamięci. De zazwyczaj implementuje ten interfejs do reprezentowania wartości właściwości w pamięci.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Ten interfejs reprezentuje samego oceniającego wyrażenie. Metodą klucza jest [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), który zwraca interfejs [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Ten interfejs reprezentuje analizowane wyrażenie gotowe do oceny. Metoda klucza jest [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) który zwraca IDebugProperty2 reprezentujący wartość i typ wyrażenia.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Ten interfejs reprezentuje wartość i jej typ i jest wynikiem oceny wyrażenia.

## <a name="see-also"></a>Zobacz też
- [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)
